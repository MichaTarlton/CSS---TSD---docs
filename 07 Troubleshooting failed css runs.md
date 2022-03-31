# Troubleshooting failed css runs

## Typical troubleshooting of css
Typically we can just read the output from css, either directly in the terminal or in the slurm output log.
Typically this will look something like:
```
Reading metadata files
Failed to read/validate metadata file /cleansumstats/input/GIANT_HEIGHT_2018_UKB.cleansumstats_meta: - $.path_sumStats: does not match the regex pattern ^[a-zA-Z0-9][a-zA-Z0-9_.-]+\.gz$
```

or

```
N E X T F L O W  ~  version 21.12.1-edge
Launching `/cleansumstats/main.nf` [berserk_shockley] - revision: ef09f3f0cb
No such file: /cleansumstats/outdir/pipeline_info/execution_trace.txt.3
```

Once you have this you can begin to troubleshoot.


## CSS tmp directory
In cases where the issue is not entirely clear from the initial output, we may need to take a look at the temporary files to gain more insight.
Cleansumstats, in its natural state, will create a `tmp` folder in its own directory which it uses to do on the fly scratch work, i.e. where it puts files that are not to be saved but are used during processing.

Specifically, there is the folder `fake-home` which will contain the partially completed files. Normally CSS deletes this file entirely once it has exited processing. However, we can save the scratch work directory by specifying the `-w` input command and specifying the directory.

**E.g.:**
```shell
./cleansumstats.sh \
-i ${PLACE} \
-d /cluster/projects/p697/users/michaejt/cleansumstats/out_dbsnp \
-k /cluster/projects/p697/users/michaejt/cleansumstats/out_1kgp \
-o ${OUT}/cleansumstats/${id} \
-w $SCRATCH/work
```

The above example is pulled from a job script where we have defined `$SCRATCH` as the output location we want.
Using this we can check the output of CSS and troubleshoot any errors that were not already visible in the output.

## Example slurm job for troubleshooting
```shell
#!/bin/bash
#SBATCH --job-name=SUMSTAT
#SBATCH --account=p697_norment
#SBATCH --time=4:00:00
#SBATCH --ntasks=1
#SBATCH --mem-per-cpu=8000M
#SBATCH --cpus-per-task=16
#SBATCH --array=52,54,33,35,92,96,98


NUM=$SLURM_ARRAY_TASK_ID
echo ${NUM}

##export CLEANSUMSTATS=/tsd/p697/home/p697-michaejt/cleansumstats
##export CLEANSUMSTATS=/cluster/projects/p697/projects/cleansumstats.jan2022

export CLEANSUMSTATS=/cluster/projects/p697/projects/cleansumstats
export RAW=/cluster/projects/p697/projects/SUMSTATv2_RAW

##export OUT=/tsd/p697/home/p697-michaejt/cleansumstats/SUMSTATv2_OUT
export OUT=/cluster/projects/p697/users/michaejt/SUMSTATv2_dev
export LIST=/tsd/p697/home/p697-michaejt/p697code/uncleanedlist.txt


export uncleanedlist=$(sed "${NUM}q;d" ${LIST})
echo ${uncleanedlist}
export PLACE=$(find ${RAW} -type f | grep -E ${uncleanedlist}.*cleansumstats_meta)
echo ${PLACE}

export id=$uncleanedlist
echo ${id}


mkdir ${OUT}/cleansumstats/${id} ## In theory I don\t need this ## for the array test its just in case
mkdir /tsd/p697/home/p697-michaejt/p697code/scratch/${id}

##cleanup "cp -r $SCRATCH/work /cluster/projects/p697/user/p697-michaejt/scratch/${id}"



source /cluster/bin/jobsetup

set -o errexit

test $SCRATCH && module load singularity/3.7.1 ## this modification is for slurm only
##module load singularity/3.7.1  ## for running piecemeal

cd ${CLEANSUMSTATS} && ./cleansumstats.sh \
-i ${PLACE} \
-d /cluster/projects/p697/users/michaejt/cleansumstats/out_dbsnp \
-k /cluster/projects/p697/users/michaejt/cleansumstats/out_1kgp \
-o ${OUT}/cleansumstats/${id} \
-w $SCRATCH/work

cp -r $SCRATCH/work /cluster/projects/p697/users/michaejt/scratch_out/${id}


cd ${OUT}/cleansumstats/${id}/ && paste <(zcat cleaned_GRCh37.gz) <(cut -f 5- <(zcat cleaned_GRCh38.gz) ) | gzip > cleaned_GRCh37.sumstats.gz

```

> [!NOTE] 
> In this job we use the variable automatically created by slurm to refer to its own scratch directory `$SCRATCH`. Later on in the job script we instruct slurm to copy the temporary file to a different directory where we can review the output: 
> `cp -r $SCRATCH/work /cluster/projects/p697/users/michaejt/scratch_out/${id}` 

## Examples and Common Problems
### Making Changes to Metadata and Sumstats Files
Just before we begin addressing specific solutions, I just want to emphasize changes to the “live” data should not be done unless communicated to the rest of the team beforehand. In addition to this we keep changes made to the metadata (and possibly the sumstat data) files documented in the [Precimed GWAS_SUMSTATS GitHub Repo](https://github.com/precimed/GWAS_SUMSTAT) ([[precimed.SIMU README|Readme local copy here]]). Any changes should be cleared with the team and then committed to the repo. I have more information on the [[GWAS_SUMSTAT]] page.

###  Issues Reading Metadata Files
In the first section here we gave an example where CSS had problems reading the metadata file due to an illegal character in its RegEx filter: `does not match the regex pattern ^[a-zA-Z0-9][a-zA-Z0-9_.-]+\.gz`. In the cases we found, this could be due to a character like `+` being in the metadata or the sumstats filename. In this case we would just need to change the offending character to something CSS can parse (such as an underscore `_`) in the places it occurs.

> [!NOTE]
> **RegEx is short for [Regular Expressions](ADD LINK HERE)**, a useful coding tool for selecting certain patterns or characters in text. Chances are you’ve been using them already, e.g.: “`*.cleansumstats_meta`“ means “Any text `*`, ending with `.cleansumstats_meta`”. I highly recommend looking up some simple examples for when you may want to find-and-replace 20+ occurrences of something in a text file (Most modern text editors such as *Sublime Text* or *Visual Studio Code* support this feature). You can do this by googling exactly what you want do with regex and learning from there. I have included some examples in the [[00 CSS cheat sheet]] page.

Some other examples in issues with CSS reading the metadata files include **“number found, integer expected”** or **“null found, string expected”**. In the first case, the error was caused by a field in the metadata file using the wrong number format, e.g. `MAGIC_GLYCEMIC_2021_FI_HISP.cleansumstats_meta`:
``` YAML
stats_TotalN: 281416.0     # WRONG
stats_TotalN: 281416       # CORRECT
```
In this case we would just need to change it to the correct number format in the metadata file.

In the second case, **“null found, string expected”**, this was found in the **NORMENT_BRAINSTEM** sumstats, where the header for the chromosome column in the sumstat data file is named as `#CHROM` which would be fine except for that the format the metadata files are written in, **YAML**, interprets `#` as an escape character. Meaning, anything written on a line after `#` is not read by the interpreter. So CSS when trying to read `col_CHR: #CHROM`, read it instead as the `col_CHR:` being blank. 

The solution in this case is slightly different from the ones above in that we need to make changes to sumstat data file itself, change the header name to something compatible, and *then* update the metadata file.  

#### Solutions: Metadata Issues
With a minor exception of the third example. All these problems can be fixed by making minor edits to the metadata or the filenames. You can test this using your sandbox before committing changes to the live inventory. If everything goes without issue, you can then add you changes and commit them to the [Precimed GWAS_SUMSTATS GitHub Repo](https://github.com/precimed/GWAS_SUMSTAT).

[Precimed GWAS_SUMSTATS GitHub Repo](https://github.com/precimed/GWAS_SUMSTAT)


### Issues with the Sumstat Data Files

Encountering errors stemming from the sumstats data file tend to be more ambiguous, varied, and more unique in their troubleshooting approach. For instance the error messages we would normally encounter when running CSS are less informative. E.g.:
```
gzip: stdout: Broken pipe
/cleansunstats/bin/check_and_format_sfile.sh: line 86: [: too many arguments one or more problems detected with the meta data format, see logfile

tr: write error: Broken pipe

.command.run: line 23: echo: write error: Broken pipe
```

Assuming we initially encountered the error while running css as a slurm job, we may be able to first investigate by running the file with css as a standalone job in our terminal on TSD. 

Either way we run it, we will want to ensure we obtain a copy of cleansumstats’ working directory as directed above. The css terminal output, slurm log, or nextflow log (as shown below), will mention the placement of the default work directory, which will look something like `/cleansumstats/work/3d/<”longhexnumber">`. Looking into the work directory we specified to css using the `-w` option, we can find a log file called `check_sumstat_format_sumstat_file.log` which will have an output like:

```
something failed during basic checks, not proceeding to testing the whole file
gziptest_result ok
tab_sep_result1 ok
one_field_header_result1 ok
one_field_header_result2 ok
tab_sep_NF_result1 fail ::: not all rows had same number of fields after tab enforcement
tab_sep_NF_result2 ok
```
See a full example in [[check_sumstat_format_sumstat_file.log]]



We can also investigate the NEXTFLOW log files for more information on the error. This will have a default path of `cleansumstats/tmp/fake-home/.nextflow.log`. There will be several nextflow log files if css has been multiple times. The most recent log will be the one without numbering, and the oldest log will have the highest number. Each log is incremented one number higher with each run. This will show a longer output but will end with an error message like:
```
Mar-02 13:56:14.255 [Task monitor] DEBUG n.processor.TaskPollingMonitor - Task completed > TaskHandler[id: 2; name: check_sumstat_format (1); status: COMPLETED; exit: 1; error: -; workDir: /cleansumstats/work/3d/5d47d6f9de0144058ba1d6f6034261]
Mar-02 13:56:14.280 [Task monitor] ERROR nextflow.processor.TaskProcessor - Error executing process > 'check_sumstat_format (1)'

Caused by:
  Process `check_sumstat_format (1)` terminated with an error exit status (1)

Command executed:

  # Sumstat file check on first 1000 lines
  echo "$(head -n 1000 < <(zcat BroadABC_METALoutput_Combined.tbl.gz))" | gzip -c > check_sumstat_format__sumstat_1000_rows
  check_and_format_sfile.sh check_sumstat_format__sumstat_1000_rows check_sumstat_format__sumstat_1000_rows_formatted check_sumstat_format__sumstat_1000_rows_formatted.log
  
  # Make second sumstat file check on all lines
  check_and_format_sfile.sh BroadABC_METALoutput_Combined.tbl.gz check_sumstat_format__sumstat_file check_sumstat_format__sumstat_file.log
  
  # Process before and after stats (the -1 is to remove the header count)
  rowsBefore="$(zcat BroadABC_METALoutput_Combined.tbl.gz | wc -l | awk '{print $1-1}')"
  rowsAfter="$(wc -l check_sumstat_format__sumstat_file | awk '{print $1-1}')"
  echo -e "$rowsBefore	$rowsAfter	Force tab separation" > check_sumstat_format__desc_force_tab_sep_BA.txt

Command exit status:
  1

Command output:
  (empty)

Command error:
  
  gzip: stdout: Broken pipe
  /cleansumstats/bin/check_and_format_sfile.sh: line 86: [: too many arguments
  one or more problems detected with the meta data format, see logfile

Work dir:
  /cleansumstats/work/3d/5d47d6f9de0144058ba1d6f6034261
```
See the full example in [[BROADABC_ASB_2017- nextflow logfile]]


#### Troubleshooting Common Problems
The quickest way to troubleshoot an issue perhaps stemming from the sumstat file is to open the file directly, either in the terminal or using pandas in a Jupyter notebook, and looking for easily identifiable common problems with the sumststats files.

These include issues such as: 

##### File is not TAB Seperated
CSS requires data files are tab delimited files (often with the file extension **.TSV)**. Meaning, files that are delimited by commas (i.e. comma separated values or **.CSV**) or have unintended whitespace delimiters in the file (that is, accidental “space characters” where they shouldn’t be) cause a misread of the file.

In this case the solution is to apply a small python script in order to effect the wanted change, whether that is “stripping the whitespace”, converting to a tab delimited table, or something else. We will give some python examples in the Python section **(MIKE PLEASE DO THIS BEFORE YOU LEAVE)**

> [!NOTE]
> All our sumstat files are zipped and so will have a filename that looks like `filename.tsv.gz` or even `filename.csv.gz`. **What I am getting at here is the only file extension that matters is the `*.gz`**
> 
> This can be confusing but the part where the filename extension contains `*.TSV` or  `*.CSV` is mostly irrelevant, and the file itself could be any format. And indeed there are several files which have already been processed from comma-delimited files to tab-delimited files, *but* were saved with their original filename extension `*.csv` . **The only way to check for sure is to open and view the file data.** 

##### File is Missing a Header
Not sure this is what I meant to add here. This is obviously more difficult.
Gleda will be working on this, the obvious solution is to check the metadata and the readme then manually attach a new header, perhaps using pandas though there certainly are options with which to do it in bash.

