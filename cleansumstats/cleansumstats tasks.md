# cleansumstats tasks
#norment #SLURM

##  ToDo:
- [ ] familiarize yourself with data context
	- [ ]  So look at input v. output data 
- [x] Wrap it into a slurm job
- [ ] Look at the input metadata and use that to inform your GWAS study
	- [ ] btw this would be sort of difficult as the input data, by context of this project, varies greatly.
	- [ ] Better idea would be to look out the output types 
- [x] Figure out how to export files from TSD
	- [ ] Would probably be handy for looking at some of those files
	- [ ] You do have permission
	- [ ] see https://data.tsd.usit.no
- [ ] Make simple script for fixing header of files that had problems and then upload that to TSD
	- [ ] Files in question are listed below
	- [ ] The specifics of how they will need changing will need to be investigated
	- [ ] for instance what will need to be plugged into a header
- [x] Email Nadine about sumstats that can be depreciated
	- [x] GAMEON_COLON_2015_CORECT
		- [x] Lol fixed anyway
	- [x] GAMEON_BREAST_2013_BCAC
- [x] Run “Broken Pipe” piecemeal 
	- [ ] See the below for more info, not entirely finished
- [ ] Email Jesper
	- [ ] What’s up with the temp directory, is it possible to use a different folder as the scratch directory
		- [ ] Not sure about this as it’s mostly obviated by the -w option
	- [ ] CSV files supported?
	- [ ] 
	- [ ] 
- [ ] 

## Working Directories and SSH addresses
Because I keep needing an easy copy/paste

Appnode address - the ones in the wiki are wrong:
`p697-appn-norment01`

My NREC user dir: `michealt@comorment:/nrec/space/michealt/github/BioPsyk/cleansumstats

“live” sumstat project folder
`/cluster/projects/p697/projects/SUMSTATv2_dev/`
`/cluster/projects/p697/projects/SUMSTATv2_RAW/`

 Personal remote folder
`/cluster/projects/p697/users/michaejt/` -

Personal home folder - easier to access from file explorer
`/tsd/p697/home/p697-michaejt/p697code/` 



## Code Snippets
Put in sublime text file here [cleansumstats code snippets](file:///%2Fhome%2FMike%2FInsync%2Fm%40tarlton.info%2FGoogle%20Drive%2F05.%20Obsidian%2FObsidian%2FCharlie%20Vault%2F20.%20Academia%2F01%20NORMENT%2FCode%20Snips%2Fcleansumstats%20code%20snippets.txt)
Also see this folder for [[slurm job template from pythopn script]] in the same folder
Skipped halfway through

Ok so for the part where I need it to list the directory

echo */  ## Lists the directories in folder

echo */ | wc -w ## counts them and returns the number

So if I set a variable to be the lilst and another variable to count form 1 to end of that list and pass that into the input

BASH VARIABLES
SIZE=`echo */ | wc -w` ## The ` ` set the output of that command to the variable

LIST=`echo */`

---

## [[30.03.22]]
Have I documented how my current slurm job works?
And how we are making changes to the documents to troubleshoot them?

Running **92 PGC_MDD_2018_no23andMe** appears to be working. 
Running under the **Testing Jobs** tab in my redhat terminal
Make sure to check it tomorrow, run the concat function, and then move to final


## [[29.03.22]]
Mostly documenting everything over at the [[7.1 Troubleshooting uncleaned sumstats]] As I have been working on fixing those and it’s better track their status there.


### PGC_ADHD_2022
moved to my sandbox raw folder
moved a copy of the sumstat head and the pdf readme (wtf)

Going to find a similar PGC metadata and copy that to my sandbox then create an edit of that




## [[28.03.22]]


Ok moved the following files to my **SUMSTATv3_FINAL** folder:
20 BCX_Blood_2020_EOS_EA
21 BCX_Blood_2020_HGB_EA
22 BCX_Blood_2020_LYM_EA
23 BCX_Blood_2020_MCHC_EA
24 BCX_Blood_2020_MCH_EA
25 BCX_Blood_2020_MCV_EA
26 BCX_Blood_2020_MON_EA
27 BCX_Blood_2020_MPV_EA
28 BCX_Blood_2020_NEU_EA
29 BCX_Blood_2020_PLT_EA
30 BCX_Blood_2020_RBC_EA
31 BCX_Blood_2020_RDW_EA
32 BCX_Blood_2020_WBC_EA
35 COGENT_COG_2017
36 COGENT_COG_2017_noCHARGE
38 EAGLE_ADHD_2016_noGC
48 IPDGC_PD_2018
76 MAGIC_GLYCEMIC_2021_HbA1c_HISP
89 PGC_CM_2020_noUKB
90 PGC_CM_2020_withUKB
97 UKB_BP_2020_SBP_withICBP_withMVP



## [[25.03.22]]
Trying to move all the finished sumstats into a new sandbox folder `SUMSTATv3_FINAL` before I finish

Currently cloning GWAS sumstats to NREC so I can try porting it over to my cluster and then pull all the good metadata into the finished container

s3cmd did not work. Permission issue?
TACL also did not work almost definitely permissions 
```
uploading directory GWAS_SUMSTAT/  
GWAS_SUMSTAT//README.md |################################| 100%  
GWAS_SUMSTAT//.gitignore |################################| 100%  
GWAS_SUMSTAT//yaml_to_csv.ipynb |################################| 100%  
GWAS_SUMSTAT//SUMSTAT_DEMO.job |################################| 100%  
GWAS_SUMSTAT//make_sge.py |################################| 100%  
GWAS_SUMSTAT//raw-metadata.yaml |################################| 100%  
GWAS_SUMSTAT//make_slurm.py |################################| 100%  
GWAS_SUMSTAT/.git/index |################################| 100%  
GWAS_SUMSTAT/.git/config |################################| 100%  
GWAS_SUMSTAT/.git/HEAD |################################| 100%  
GWAS_SUMSTAT/.git/packed-refs |################################| 100%  
GWAS_SUMSTAT/.git/description |################################| 100%  
GWAS_SUMSTAT/.git/logs/HEAD |################################| 100%  
405 Client Error: Method Not Allowed for url: https://api.tsd.usit.no/v1/p697/files/stream/p697-member-group/GWAS  
_SUMSTAT/.git/logs/HEAD?group=p697-member-group  
The request was unsuccesful. Exiting.
```

Fuck it we’ll do it live: using the data export import page.

Ok finally moved and unzipped the fucking thing to my sandbox in a folder called `GWAS_SUMSTAT` only moved over the metadata folder

**Next steps:**
1. Identify the correct metadata and move to your out folder
2. move the corresponding sumstats from the live RAW folder to my sandbox OUT folder and make corrections. 
3. Move corrected sumstats file pairs to my FINAL folder
4. 


## [[24.03.22]]
In regards to U92
An error in my script on line 24 something like `${id}.*cleansumstats_meta`
the `*` was in the wring place and is likely entirely unnecessary
I would bet this has to do with there being multiple sumstat sets in the folder
OK that should fix it.



## [[23.03.22]]
Ok the whole pyhton thing about to get realllllll stupid
Except I’m going the “SMRT” route and just making a script in the submit directory

```shell
python $SLURM_SUBMIT_DIR/python.py input input input
```

Well shit. That was easy if that works



## [[22.03.22]]
Ok start in your redhat instance and troubleshoot the python yaml section.
Perhaps start jupyter back up and do it there.

Need to clarify what has been worked on and what updates have been made to the live files.
Made a script to identify lines of another file by row number. See [[matchlines.sh]].
Used this to update [[7.1 Troubleshooting uncleaned sumstats]] with the actual sumstat names.

### Making Jupyter run
Ook so I keep running into an error while trying to run jupyter.
I think I have to run **EXACTLY** the same python module as what I used to install it
So: `module load  Python/3.7.4-GCCcore-8.3.0`
Jeezus cherist
Even loading a newer module and then installing did not do the trick
Myabe if I created a new py3 folder to run my environment in it’d work but fuck

---
### Making the full job script
Ok it looks like I may have it figured out. See the file `slurmjob.py_array` in your durable p697code folder, and test it in jupyter.

Ok so stesting in jupyter != in terminal. I assume the reason being that it is effectively a py3 venv

ok so I made some obvious changes in the jobscript.

In regards to getting python to run I’m setting it up to create it’s own py3 folder and venv
I may want to change this to just using an already established venv such as my personal one

**Sandeep:** You can just use a global venv such as the one in your sandbox, it is not necessary to create a new one each time

### Passing to python
The smart way would be to save what we have as a pyscript and pass the variables to that
I’m taking a more blunt approach atm since I am dumb and the script itself is small

```
import sys
import os
```
`os.environ['FILENAME']` seems to be how I pass these into python

#### Something like this would be preferable
```
#!/bin/bash
#SBATCH --cpus-per-task=1        # number of cores

cd $SLURM_SUBMIT_DIR
pwd

python $SLURM_SUBMIT_DIR/python.py HumptyDumpty.txt newhumpty.txt ad.txt
```
## [[21.03.22]]
OK I’m sick an unable to work from home today so I will try finishing the documentation.

Also can try reframing the documentation to be more general, so a wiki for just TSD users in addition to the current one.

**Created a copy of the folder [[P697code folder raw copy do not link to directly]]**

## [[18.03.22]]
### Parsing the YAML (Continued from yesterday)
Following from yesterday’s conversation with Oleks that I should probably just parse it with yaml

Looks like TSD does actually have pyyaml

```
pip install pyyaml
```


Example from https://stackoverflow.com/questions/1773805/how-can-i-parse-a-yaml-file-in-python
```
import yaml

with open("example.yaml", "r") as stream:
    try:
        print(yaml.safe_load(stream))
    except yaml.YAMLError as exc:
        print(exc)
```



## [[17.03.22]]
### Documentation project
Made some slight fixes to the slurmjob examples.
Need to work on the python stuff as the documentation is pretty garbo
Need to fix the  [[02 sumstat directory structure and files]] to include sumstat output directory structure


### Fixing 33 BROADABC_ASB_2017
[[7.1 Troubleshooting uncleaned sumstats#33 BROADABC_ASB_2017]]
I copied the sumstat files to my sandbox. There I edited the metadata and modified the data file with the below script 

In jupyter notebook I simply used 
``` python
fname = "<name of zipped file>"

import pandas as pd
df = pd.read_csv(fname, delim_whitespace=True, dtype=str)
df.columns = df.columns.str.strip()
df.to_csv('path to output file and name', sep='\t', index=False)
```

Problem is I needed to modify the cleansumstats metadata file to point at the new version

and then in the slurm job just uses the modified files as usual.

### Modifying the slurm script to incorporate this
blehhh where to start
Like Oleks said it will involve creating a temp folder where I copy the files, modify them and then move on.

I could probably do this without modifying the metadata. Does the metadata point to within the same folder?

#### slurmjob.array
Created the more general slurm job script for arrays titled `slurmjob.array`
This is basically the same as before just a little more fleshed out and with comments included.

#### slurmjob.py_array
Do I need to load the python module, probably.
Going to copy everything to a scratch subfolder
`cp -a /source/. /dest/`

I really **REALLY** do not want to have to copy the information out of the `.cleansumstats_meta` file soI think I will opt to copy *everything* from the folder even though this might cause some overhead. Looks like it may not be too bad anyway as it’s only 256mb for the one I checked out (Unclean 33).
**The worst is SANGER BLOOD which is a whopping 233gb**.

Ok pretty sure the css meta and the actual file **almost never have the same filename** (add this to the guide)

[[How to get size of directory]]
[[How to extract directory path from file path?]]
- These are actually used directly in CSS on lines 290 - 291
- See [[cleansumstats.sh]]
- I will likely use export `DIR=${PLACE%/*}` IN MY JOBSCRIPT

OH YEAH SO WHAT I WAS LOOKING FOR WAS LINES 290-293
```shell
# indir
indir_host=$(dirname "${infile_host}")
infile_name=$(basename "${infile_host}")
indir_container="/cleansumstats/input"
infile_container="${indir_container}/${infile_name}"
```
He takes the directory from our metadata location so I should be able to copy that.
But if the file is too large then I want to grab just the one file I need. 
Which means I have to parse the yaml.

#### Parsing the yaml
Well he doesn’t do this in cleansumstats.sh, sooooo onto the singularity script?
According to the regular documentation and looking at a metafile, the field we want to parse is "path_sumStats"
**I have to do this because how else would I know what to read into the pandas script…..**

Is path_sumstats always on the 4th line?

`sed "4q;d" metadata`

Cut all after 8th character
`sed -n "2p" test | cut -c 8-`

To cut from the 4th line,  everything from the 15th character onward
`sed -n "4p" <metadata> | cut -c 15-`
**this appears to work!**
**Oleks thinks this would likely break as it is not guranteed to always be on that line**


---

## [[16.03.22]]
**OK, I created [[7.1 Troubleshooting uncleaned sumstats]] and updated with the current status of all the troublshooting sumstats initially found in the uncleaned list**



Update to Confirmed in [[cleansumstats tasks#Checking the metadata files]]
  
37, 40, 41, OR column problem: **DEPRECEATED**
43,44,45: Regex: **fixed**
34,46,47: **DEPRECEATED** 
Require an effect allele column but it is not present
- Honestly unsure what to do with this
- It requires something be put in but not certain what should be
59-78: MAGIC GLYCEMIC
- Fixed all
- Replace 28140.0 with 28140

80-84: NORMENT_BRAINSTEMS
- `col_CHR: #CHROM`
- not sure what this should be changed to
- The error is `null found, string expected`

85-86: PGC_ASD_2017
As expected they are missing a header row

### Troubleshooting BROADABC_ASB_2017
See [[7.1 Troubleshooting uncleaned sumstats#33 BROADABC_ASB_2017]]
Need to copy what I did in my jupyter notebooks here.

Basically ised the python script (though i used a slightly different one to strip whitespace) from the above ss

Waiting to see how it ran.


In the meantime I’m rsyncing the jupyter ntebook location ``
`/cluster/projects/p697/users/michaejt/py3/Untitled Folder` 
with my export folder
 `/tsd/p697/data/durable/file-export/michaejt`
 So I can pull out what I did in Jupyter

Moved them to a folder here [[Jupyter Notebooks]]

## [[15.03.22]]

I am creating a new document for cleaning the remaining sumstats which did not have easy fixes.
See: [[7.1 Troubleshooting uncleaned sumstats]]

### Preprocessing step per oleks

```python
import pandas as pd
#fname - input file (sumstats.gz)
df = pd.read_csv(fname, delim_whitespace=True, dtype=str)

# strip white-space characters from column names
df.columns = [x.strip() for x in df.columns]

df.to_csv('temp.sumstats.gz', sep='\t', index=False)
```

My challenge here is to figure out how to name the on the fly temporary file and how to make this work with a temporary space.

He added a bit here where he strips the white space.

There will be more preprocessing to add eventually but we can do that iteratively

## [[14.03.22]]
Ok so doing some fixes to  the documentation project. May need to spin that off into it’s own thing.
See today’s notes in order to see what Gleda mentioned

Also may need to add the singularity module issue. I have added Oleks’ fixes for it in to all the SLURM jobs, but I need to document what to do if you run into the issue while trying to run off an login node.


### Python
Didn’t really do anything all that different except ran out of my venv in my cluster user folder. OTher wise same directions. Made small update to [[Using Python on TSD]].

### Modifying bugged sumstat files
Ok starting with **GAMEON_COLON_2015_CORECT** as I think I can make this an easy fix

Unfortunately I did not make an ez comprehensive list of “to be fixed” sumstats really. Check on 02.03.22 in this folder for some that I earmarked including thew one already mentioned.

#### GAMEON_COLON_2015_CORECT


``` python
df = pd.read_csv(filename, escapechar='\n')

df.to_csv('data.tsv', sep='\t', encoding='utf-8', index=False)
```


Created a sandbox version, also added sandbox directories for RAW and OUT called v3

well as of now it is at least running.

**LMAO YOU SHOULD HAVE RETIRED THESE. AT least you got the exercise.**

Looks like it worked anyways lmao. Ok so I have a nicely cleaned sumstat for this under my SUMSTATv3_OUT folder in my personal cluster directory. It has the metadata name of `data.tsv`.



#### Conversation with Nadine on 02.03 about keeping data
> Yes, I would keep the brainstem data. I don't think our group has done much with them yet but it will probably be used in the future. So it might be nice to include them. 
> 
> Maybe when everything is updated you can send me a final list of the sumstats that didn't work and I'll make a note of it in the inventory google doc


## [[10.03.22]]
Downloaded my p697 code folder off tsd and set it in my github folder.
Also staged it and pushed to github

Making a lot of changes to my slurm job to make it readable in documentation. Here is my full fix of it that I am keeping all the troubleshooting parts in: [[cleansumstas slurm job template 10.03.22]]

Leaving off in my review of this document around the 17th as that’s where I start getting into the NREC

## [[09.03.22]]
[[Using Python on TSD]]
```
cd /cluster/projects/p697/users/michaejt/
mdir py3
module spider python
module load python3.gnu/3.7.3
python3 -m venv .
```

ANNDDDD getting errors.
Apparently it’s not just me it’s a project wide problem per Sandeep, but he has not specified how, what, or why.
Apparently a file issue might be fixed now.


#### Modify slurm script with this!
```shell
test $SCRATCH && module load singularity/3.7.1
```
Per Oleks

## [[08.03.22]]
Ok so the problem may be with the fact I installed it on the login node or as I put it “in the durable directory”
¨Try installing on the cluster as the directions specify and come back at it


## [[07.03.22]]
So I created a python install at `/tsd/p697/home/p697-michaejt/py`


## [[05.03.22]]
### Working on getting python going on TSD
https://wiki.norment.uiocloud.no/dokuwiki/tsd_software
https://www.uio.no/english/services/it/research/sensitive-data/help/software/python.html

! [[Using Python on TSD]]

Creating a python virtual environment in my personal home folder
`module load python3.gnu/3.7.3`
- I don’t know if this is the “correct” version

`python3 -m venv /tsd/p697/home/p697-michaejt/p697code/py`

Taking from [[Using Python on TSD#clean install jupyter in a new environment]]:
`cd py`
`source bin/activate`
- Probably should have put this in `/cluster/projects/p697/users/p697-michaejt/py3/bin/activate`
- They specifically say it is best to run on cluster
- Per conversation with Sandeep this could be the reason it is not working

```
pip3 install numpy
pip3 install pandas
pip3 install scipy
pip3 install matplotlib
pip3 install statsmodels
pip3 install numdifftools
pip3 install matplotlib_venn
pip3 install jupyter
```

### Conversation with Oleks needing this
[Oleksandr Frei](https://app.slack.com/team/URSK9HNCW)  [2:13 PM](https://norment.slack.com/archives/D02PQ7L8H8F/p1646399586853009)  
> not all rows had same number of fields after tab enforcement”

Thanks for digging this message, it seem that’s the key. Have you checked input files - are they tab or comma separated?

[Michael Tarlton](https://app.slack.com/team/U02PQ74TGCX)  [2:13 PM](https://norment.slack.com/archives/D02PQ7L8H8F/p1646399627081929)  
From what I recall from two days ago it was tab

[Oleksandr Frei](https://app.slack.com/team/URSK9HNCW)  [2:16 PM](https://norment.slack.com/archives/D02PQ7L8H8F/p1646399778039389)  
Most likely yes - I’ve checked my old records and it’s only cancer-related GWAS that had comma separator

there is a subtle difference between tab-separated and whitespace-delimited files - could it be the reason?

`delim_whitespace=False`

[https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html)
previously I read all data using pandas’ read_csv function, with delim_whitespace=True option

---
[Oleksandr Frei](https://app.slack.com/team/URSK9HNCW)  [2:19 PM](https://norment.slack.com/archives/D02PQ7L8H8F/p1646399953768589)  

we could add a pre-processing step in python like this:
``` python
import pandas as pd  
pd.read_csv(input_path, delim_whitespace=True, dtype=str).to_csv(‘temp_file.csv’)
# and then use temp_file.csv as input for cleansumstats.sh

pd.read_csv(input_path, delim_whitespace=True, dtype=str).to_csv(‘temp_file.csv’, index=False, sep=‘\t’)

#(small update - to_csv should include  “index=False” and “sep=‘\t’ )
```

## [[02.03.22]]
### Yesterday’s Notes from review of sumstats issues with Oleks
When troubleshooting issues with a sumstats file/folder, one evenue of troubleshooting would be to view the files in associated folder.

E.g.: 
#### **PGC_ASD_2017**
Needs a new header, we can see what that should look like from going through the readme in the folder. There may also be some documentation from Oleks with specifics regarding the context of the files.

This is where I will need to create a python script to insert a header

Make sure you create a note along with this that is attached in the RAW folder

Header names are the same as in the readme file? There looks like there may be some slight differences.

#### GAMEON_COLON_2015_CORECT
OR col issue

The file is CSV but CSS is processing everything as TSV

Need to see if CSS supports CSV

Assuming **GAMEON_BREAST_2013_BCAC** is a similar issue

#### COGS_PROSTATE_2013
Similar issue however not actually the OR col.
It is also in CSV form
Oleks says to consider depricating this as it is old data and perhaps not worth the effort.

Also to be considered legacy is:
**BWGN_T1D_2009**
**ICBP_DBP_2011
ICBP_PD_2011**


---
#### Norment Brainstem Inventory
Issue with these files appear to be the `#CHROM` header on the chromosome column. Specifically the `#` is throwing an error, as the YAML meta file interprets it as a comment escape character.

The easiest fix would be to change the header title in both the data file(s) and the meta file.

Make a comment somewhere, some documentation that directs submitters to not do this (perhaps flesh out what can’t go in YAML files)

Also, note there are multiple files here and we would only need ot update the 3 most recent ones. The others are previous versions.

There was also some issue with how there were three allele columns in these files, but I’m a little uncertain as to what the problem was.

---
#### Rerunning “BRoken PIpe” errors
Using Uncleaned-33: **BROADABC_ASB_2017**

For some reason this is taking forever at the part where it finds the appropriate meta files
Literally the find script

Where is the log file ???
/cluster/projects/p697/projects/cleansumstats/tmp/fake-home/.nextflow.log
there are several nextflow.logs. the most recent one is the one without numbering. They appear to work by incrementing the number of older logs

I copied the output to /tsd/p697/home/p697-michaejt/p697code/unclean33

I put two outputs there, one was directly from the terminal, the other is from the nextflow log

The log mentions the work directory being /cleansumstats/work/3d/”toolongahextowriteout”

Going into here there is a log file called `check_sumstat_format_sumstat_file.log` which I have saved to the uncleaned33 folder.
This mentions a tab separation failure “not all rows had same number of fields after tab enforcement”

What’s up with the broken links in this directory?


## [[01.03.22]]
From the general error that seems to afflict 15 sumstats files
something about “broken pipe”
```
# Sumstat file check on first 1608 lines

echo "$(head -n 1008 < <(zcat Psoriasis.meta.gz))” | gzip -c > check_sumstat_format__sumstat_1086_rows

check_and_format_sfile.sh check_sumstat_format__sunstat_1668_rows check_sumstat_format_sumstat_1006_rows_formatted check sumstat_format__sumstat_1066_rows_formatted.log # Make second sumstat file check on all lines

check_and_format_sfile.sh Psoriasis.meta.gz check _sumstat_format_sumstat_file check sumstat_format_sumstat_file.log

# Process before and after stats (the -1 is to remove the header count)

rousBefore="$(zcat Psoriasis.meta.gz | wc -1 | awk *{print $1-1}")"

rowsAfter="§(wc -1 check_sumstat_format__sumstat_file | awk ‘{print $1-1}")"

echo -e "$rowsBefore $rowsAfter Force tab separation” > check_sumstat_format_desc_force_tab_sep BA.txt
```

Also:
```  
gzip: stdout: Broken pipe
/cleansunstats/bin/check_and_format_sfile.sh: line 86: [: too many arguments one or more problems detected with the meta data format, see logfile

tr: write error: Broken pipe

.command.run: line 23: echo: write error: Broken pipe
```



## [[28.02.22]]
### Fixing running CSS piecemeal
I’m using the wrong instance of Singularity on the appnode
Using the MODULE LOAD SINGULARITY
Which is the cluster instance, you need to load the loacla version
make sure you purge the module

`modulde list` to purge the cluster instance of singularity in case that has been loaded 
`which singularity` to see which version is runnning

Ok maybe putting this on the back-burner for a little while

### Reviewing list of general error outputs

Immediately looking at the error output for a few of the failed CSS files

A few were about some sort of file lock failing or permission denied error

So rerunning those.

### Results of the rerun scripts
None of them returned the same issue
One was fixed, the rest returned either the *Broken Pipe* error or a *No Such File* error

### Changes to slurm script
Also commented out the `cleanup` command in the slurm script as that doesn’t appear to do anything useful atm

Oleks instead suggested that I pass the scratch command into CSS and then copy that out?

I wasn’t entirely clear

Reminder that the home folder, your p697code is not really accessible by the cluster


### Checking the metadata files
Ok so see the [GWAS_SUMSTAT repo](https://github.com/precimed/GWAS_SUMSTAT/tree/master/cleansumstats_meta) with the metadata files.
The idea here being that you need to be able to edit these as you see fit and then reupload them to the TSD

Do I already have these on my mxlinux

I do! `/home/Mike/github/precimed/GWAS_SUMSTAT/`

Ok so start going through them

Made myself a branch of the GWAS_SUMSTATS and I am applying fixes to the metadata there

Where did I leave the list of IDs for the failed list?
As referenced in the slurmjob: `p697code/uncleanedlist.txt`

Jobs which failed due to an error in the 
**See the file in your code folder on this subject**
37, 40, 41, OR column problem: not sure
43,44,45: Regex: fixed
34,46,47: require an effect allele column but it is not present
- Honestly unsure what to do with this
- It requires something be put in but not certain what should be
59-78: MAGIC GLYCEMIC
- Fixed all
- Replace 28140.0 with 28140
80-84: NORMENT_BRAINSTEMS
- `col_CHR: #CHROM`
- not sure what this should be changed to
- The error is `null found, string expected`

85-86: PGC_ASD_2017
As expected they are missing a header row

Hey look github does a better job of laying this out:
https://github.com/MichaTarlton/GWAS_SUMSTAT/commit/f34d1a42b58536a0fd4f6a582866c5eda764c062





### See also the `Makefile` bash script that Oleks made, located in `/cluster/projects/p697/projects/SUMSTATv2_dev/Makefile`
```  shell
cleansumstats_meta.tar.gz:
		find . -name '*.cleansumstats meta’ -print0 | tar -czvf cleansumstats meta.tar.gz --null --files-from -

.PHONY: cleansumstats_meta.tar.gz
```
This script appears to grab, zip the meta files

### NREC stuff
I have been given access to the dashbaord
OK lol now what do I do with it

#### NREC API ACCESSS
Username: 'michaejt@uio.no'
Password: '8XscCg0wLR0LB4Po'

---

Remember the thing about updating the css metadata files from github

## [[26.02.22]]
Probably referenced on a previous day. I can’t run the CSS piecemeal in shell. I keep running into the error:
`ERROR : No setuid installation found, for unprivileged installation use: /mconfig - without-suid Connection to p697-appn-normento1 closed. (`

Discussing it with Sandeep he suggested the following:
> 
> For runnng the comorment container for mixer analysis, I had to save these variables in bashrc file (as an example):
```
export COMORMENT=/cluster/projects/p33/github/comorment  
export SIF=/cluster/projects/p33/github/comoroment/containers/singularity  
export SINGULARITY_BIND="$COMORMENT/containers/reference:/REF:ro,$COMORMENT/containers/matlab:ro,$COMORMENT/reference:/REF2:ro"
```
> perhaps, that could be the reason?
> 
> [https://github.com/comorment/containers/blob/main/usecases/mixer_real/MIXER_REAL.job](https://github.com/comorment/containers/blob/main/usecases/mixer_real/MIXER_REAL.job)
> 

I tried following the advice, but of course I do not have the permissions to change that file. 

Look at the repo he linked you to and see if there are some input options you can use when running.

**FIX: MODULE PURGE**
**DO NOT RELOAD SINGULARITY AFTERWARDS**



## [[23.02.22]]
Ok so based on yesterday’s conversation.

Going to run the script from the redhat server since putty keeps crashing

Rerunning it from redhat leads to: 
> ERROR : No setuid installation found, for unprivileged installation use: /mconfig - without-suid
Connection to p697-appn-normento1 closed.

I’m guessing this is some sort of permissions issue I’m getting
What happens if I run the same thing for a successful  file?

uncleanlist  definition command is not working and I don’t know why

**FIX: MODULE PURGE**
**DO NOT RELOAD SINGULARITY AFTERWARDS**

## [[22.02.22]]
Ok so I successfully ran the 98 (minus 23 and me files) files which failed, last night

I'm going through the slurm outputs right now

Summary: 20 files were successfully run using the new CSS

####  Slack Conversation with Oleks 
![[Slack Conversation with Oleks 22.02.22]]

## [[21.02.22]]
Testing out the other two sumstats:

### IPDGC_PD_2018  
Well the job is kicking off so it’s not the metadata file
Oddly threw no errors until the end but that was because of my slurm job


### GIANT_HEIGHT_2018_UKB
I am betting this is because of the `+` in the .gz file it points to


**So!** How many have to do with a ‘+’?

See **pluslist.txt** on the win machine of all files with  this problem.

### Uploading 1.3.0 to TSD
Don’t need the API
Check the terminals to see what Oleks did 
Apparently the file was not too large, and we can instead zip it and move it to my machine then upload it via data.tsd.usit.no

### Coversation with Oleks
Introduced me to a tool in the [precimed.GWAS_SUMSTAT repo](../../yaml_to_csv.ipynb) the yaml_to_csv.py script.

Basically a way to batch edit the meta info files and then port them back and keep the repo updated

He made a branch under your github, maybe go take a look at that
A WHOLE THING I GOTTA COVER LMAO INCLUDING LEARNING THE FUCK OUTTA GIT

### Rerun the  CSS 1.3.0
Going to run it only on the files which failed which means I still need to make an iterative script.{}

working from the SUMSTAT_RAW folder (so make a cd command) this return s the folder and metafile path
`find . -type f | grep -E ${uncleanedlist}.*cleansumstats_meta`


`/tsd/p697/home/p697-michaejt/p697code/uncleanedlist.txt`


`sed 'NUMq;d'`

Have to use  \double quotation marks for the variable to work in sed.
`sed "${NUM}q;d" /tsd/p697/home/p697-michaejt/p697code/uncleanedlist.txt`
${NUM}

and set NUM= array

SO:
`uncleanedlist=$(sed "${NUM}q;d" /tsd/p697/home/p697-michaejt/p697code/uncleanedlist.txt)`

`PATH=$(find /cluster/projects/p697/projects/SUMSTATv2_RAW/ -type f | grep -E ${uncleanedlist}.*cleansumstats_meta)`


---
NOpe no tht ebelow, loops, doesn’t iterate Nth
```
NAMES="$(< /tsd/p697/home/p697-michaejt/p697code/uncleanedlist.txt)"
for NAME in $NAMES; do
    echo "$NAME"
done
```


## [[18.02.22]]
Creating a new cleansumstats repo in my local windows folder so I can output tmp files there.
I would just redirect the temp files however that seems to not be an option.
I think I will rsync the cleansumstats directory to the local win machine so I can troubleshoot there. 
Also I will be able to see the old slurm jobs I ran
They look super different.

Make sure you direct the slurm job to large excluded folders on the remote working directory

I will exclude the `./out_dbsnp` and the `./out_1kgp`
As well as the `./tmp` folder
So:
``` bash
rsync -avP --exclude={'out_dbsnp','out_1kgp','tmp'} /cluster/projects/p697/users/michaejt/cleansumstats /tsd/p697/home/p697-michaejt
```

**DOUBLE CHECK THAT YOU ARE USING THE SAME OPTIONS AS OLEKS**
*(or maybe you don’t need to? after all it’s disconnected from the original source)*
Yeah don’t worry it’s one-way not dual laned.
``` bash
rsync -avP cluster/projects/p697/projects/cleansumstats /cluster/projects/p697/users/michaejt
```

`-a` is Archive
> tells rsync to syncs directories recursively, transfer special and block devices, preserve symbolic links, modification times, groups, ownership, and permissions.

`-v, --verbose      `         
> increase verbosity
> This option increases the amount of information the daemon logs during its startup phase. After the client connects, the daemon's verbosity level will be controlled by the options that the client used and the lqmax verbosityrq setting in the module's config section.

`-P`, equivalent to `--partial` `--progress`. 
> When this option is used, rsync shows a progress bar during the transfer and keeps the partially transferred files. It is useful when transferring large files over slow or unstable network connections.

https://linuxize.com/post/how-to-exclude-files-and-directories-with-rsync/
https://linuxize.com/post/how-to-use-rsync-for-local-and-remote-data-transfer-and-synchronization/
https://linux.die.net/man/1/rsync

---
#### Modifying the SLURM job for troubleshooting

See if you can import the slurm job that seem sto be saved on the machine
Menaawhile here is ![[Olek's Template CleanSumStats SLURM job]]
So modifying this bad boy .:
``` bash
#!/bin/bash
#SBATCH --job-name=SUMSTAT
#SBATCH --account=p697_norment
#SBATCH --time=4:00:00
#SBATCH --ntasks=1
#SBATCH --mem-per-cpu=8000M
#SBATCH --cpus-per-task=16

source /cluster/bin/jobsetup

set -o errexit

module load singularity/3.7.1

export CLEANSUMSTATS=/tsd/p697/home/p697-michaejt/cleansumstats
export RAW=/cluster/projects/p697/projects/SUMSTATv2_RAW
export OUT=/tsd/p697/home/p697-michaejt/cleansumstats/SUMSTATv2_OUT

## not in original(taken out of make_slurm.py)
export sourcedir=SSGAC_RISK_2019
export id=SSGAC_RISK_2019

cd ${CLEANSUMSTATS} && ./cleansumstats.sh \
-i ${RAW}/${sourcedir}/${id}.cleansumstats_meta \ 
-d /cluster/projects/p697/users/michaejt/cleansumstats/out_dbsnp \ 
-k /cluster/projects/p697/users/michaejt/cleansumstats/out_1kgp \
-o ${OUT}/cleansumstats
--dev ## not sure about this from the developer instructions

cd ${OUT}/cleansumstats/${id}/ && paste <(zcat cleaned_GRCh37.gz) <(cut -f 5- <(zcat cleaned_GRCh38.gz) ) | gzip > cleaned_GRCh37.sumstats.gz

```
**Notes:**
`export` makes the variable available everywhere

`--dev` not sure about this from the developer instructions. Possibly a slurm input command.

`sourcedir=` SSGAC_RISK_2019
`id=` SSGAC_RISK_2019
`id=` SSGAC_RISK_2019_PC1
Two options here. Go for the first.

**ALSO:** The double curly brackets leads to a bad substition error. Probably python syntax not bash. Use single curly brackets. 

**Ok now submit the slurm script**
[[UIO HPC Job Submit]]

`cd /tsd/p697/home/p697-michaejt/p697code/`
`sbatch slurmjob`

And done for now.

`qsumm` queue summary
Oleks recommends using this to see which accounts are most available before running.
For instance I use P697_norment, however there appears to be several available options

---
#### Results
After some problem solving as to getting the slurm job to run, including permissions errors with the cluster project directory for my user and issues mounting CSS from my local windows directory;

We came to a real output error from CSS:
```
Reading metadata files
Failed to read/validate metadata file 
/cleansumstats/input/SSGAC_RISK_2019.cleansumstats_meta: - $.path_sumStats: does not match the regex pattern ^[a-ZA-Z0-9][a-ZA-Z\theta-9_.-]+1.gz$
```
Upon which we opened up the metadata file in question `SSGAC_RISK_2019.cleansumstats_meta` 
Oleks realized the issue was the `+`  in:
`path_sumStats: RISK_GWAS_MA_UKB+replication.txt.gz`

## [[17.02.22]]
Rerunning the new CSS 1.3.0 on the NREC box
Location of the new CSS setup:
`michealt@comorment:/nrec/space/michealt/github/BioPsyk/cleansumstats$`
Ran the test case from the [[BioPsyk.cleansumstats.README]]
So basically just ran down the installation instructions.
Everything seems above board.

Looking at the example outputs `via zcat cleaned_GRCh38.gz | head`
It seems GRCh37 is missing the data again so I’ll need to add that akin to how Olek’s does in his slurm script:
```
cd ${{OUT}}/cleansumstats/{id}/ && paste <(zcat cleaned_GRCh37.gz) <(cut -f 5- <(zcat cleaned_GRCh38.gz) ) | gzip > cleaned_GRCh37.sumstats.gz
```

How the cut function works:
clips part of a file, 
the `-f` grabs the “fields” default delimited by space.
Presumably the `5-` is to select fields 5 through end
I’m trying to figure out what the `<(...)` bullshit is, but I’m guessing part of the paste fnc
Nope, those must be some sort of “ feed into” thing like > is “output to” 

**See [[Bash Brackets Quick Reference - 17.02.22]]**
! [[Bash Brackets Quick Reference - 17.02.22#Single Parentheses https dev to rpalo bash-brackets-quick-reference-4eh6 -single-parentheses-| Single Parentheses]]
! [[Bash Brackets Quick Reference - 17.02.22#Angle Parentheses https dev to rpalo bash-brackets-quick-reference-4eh6 lt-angle-parentheses- | Angle Parentheses]]

Note that he creates a final output file called `cleaned_GRCh37.sumstats.gz`

---
**Test this sumstat file**
**96:** SSGAC_RISK_2019 
**48:** IPDGC_PD_2018
**45:** GIANT_HEIGHT_2018_UKB

The groups of sumstat files probably have similar issue

dev mode in CSS check docs for that
slurm should have some output
- Can probably remove the chkfile from my slurmjob
- It was actually causing failures of the slurm job

“There are multiple ouput folders”
Check the actual output fodlers

The cleansumstats folder I call to during the run will have a `tmp` folder with a `fake-home` folder which has the partially completed temp files. THe slurm output should tell me which folder it is upon failure of CSS

Running CSS in dev mode will ensure that the tmp files are not cleaned up

Run the old pipeline on the problem ones. But don’t spend too much time.
We are balancing this against how much time it takes to get the API nrec up and going.


## [[16.02.22]]
This project has turned from me just seeking out the missing and getting familiar with the system to  updating the CSS software on TSD

Currently the latest version is 1.3.0
We are setting me up to port that to the TSD.


OK so we are going to add me to a TSD sandbox server *NREC*
Which is like a VM server, it has internet connection
There I can import the 


#### Olek’s commands
This is for finding the processed file
```
cd /cluster/projects/p697/projects/SUMSTATv2_dev/cleansumstats find . -type f | grep cleaned_GRCh37.sumstats.gz
```
but does this mean multiple meta files get combined into a single output?
No.


**List of all  clean output files**
```
cd /cluster/projects/p697/projects/SUMSTATv2_dev/cleansumstats 

find . -type f | grep cleaned_GRCh37.sumstats.gz | sort > /tsd/p697/home/p697-michaejt/p697code/cleanedlist.txt`
```


**/tsd/p697/home/p697-michaejt/p697code/**
- Made several folder list files
- 

List all directories in current folder
`ls -d */` 

**Folder List of the SUMSTATv2_RAW folder**
`ls -d */ > /tsd/p697/home/p697-michaejt/p697code/folderlist _SUMSTATSv2_RAW.txt ` 


**List of metadata files**
Ok so the place where I was looking `/cluster/projects/p697/projects/SUMSTATv2_dev/cleansumstats` doesn’t have the meta files that would be `/cluster/projects/p697/projects/SUMSTATv2_RAW
so cd to there and then run the  
`find . -type f | grep '.cleansumstats_meta' > /tsd/p697/home/p697-michaejt/p697code/metalist.txt`

Adding a sort
`find . -type f | grep '.cleansumstats_meta' | sort  > /tsd/p697/home/p697-michaejt/p697code/metalist.txt`

**OUTCOME**
Number of folders in RAW input directory: **184**
- Not entirely important
 
Number of metadata input files: **362**
Number of cleaned output files: **264**
Meaning the total number missing is about **98**

**Metalist_woutfolders**
removing the folders leaving use with only the  metadata file names (probably could have used grep or find to do this) using the regex:
`.+?/` to select everything up until the `/`

sorted metalist_woutfolders.txt and sent to metalist_woutfolders2.txt

then, [not `diff` but instead `comm` ](https://www.networkworld.com/article/3279724/comparing-files-and-directories-with-diff-and-comm.html)to find the files present in metalist_woutfolders2.txt but not in cleanedfilelist.txt
`comm -23 metalist_woutfolders2.txt cleanedfilelist.txt > uncleanedlist.txt`

So the broken ones are in the file **uncleanedlist.txt**

checking…..

### NREC and further notes
`ssh michealt@158.39.200.231`
my name is accidentally misspelled
Set my password to my current 
Changed my mac ssh config to access the NREC box 
I can access it directly by `ssh nrec`
michealt
I have sudo so add your public ssh key from your linux machine

**On my linux machine**
First checking my keys:`$ ssh-keygen`
Creating myself a new key on linux: `ssh-keygen` with no passphrase
Creating and Modifying the ssh config file
`touch ~/.ssh/config` - create
`chmod 600 ~/.ssh/config` - give user permissions and no one else
`nano ~/.ssh/config` - open and edit
```nano
Host nrec
        HostName 158.39.200.231
        User michealt
```

**On the NREC machine**
open the auth keys file in the .ssh directory in root
`michealt@comorment:~/.ssh$ nano authorized_keys`
add my public key to an open line

Et voila I can log on from linux via `ssh nrec` open the auth keys file in the .ssh directory in root
￼michealt@comorment:~/.ssh$ nano authorized_keys￼
add my public key to an open line

Used the following articles:
https://stackoverflow.com/questions/3828164/how-do-i-access-my-ssh-public-key
[[Set up SSH public key authentication to connect to a remote system - 17.02.22]]
[[Using the SSH Config File - 17.02.22]]



### Need to save
out_dbsnp
out_1kgp
1kgp
dbsnp

from the old CSS folder jan2022

Ask Sandeep for access to the NREC dashboard

Much to remember and go over, double check your notes and hopefully the input history to your terminal on the mac will be saved

Email CSS repo author

Where is the repo located on nrec?
``` bash
michealt@comorment:~$ ls
michealt@comorment:~$ / 
bash: /: Is a directory
michealt@comorment:~$ dir
michealt@comorment:~$ dir /
bin  boot  dev  etc  home  lib  lib32  lib64  libx32  lost+found  media  mnt  nrec  opt  proc  root  run  sbin  snap  srv  sys  tmp  usr  var
michealt@comorment:~$ dir space
dir: cannot access 'space': No such file or directory
michealt@comorment:~$ dir /space
dir: cannot access '/space': No such file or directory
michealt@comorment:~$ dir nrec/space
dir: cannot access 'nrec/space': No such file or directory
michealt@comorment:~$ cd  /nrec/space
michealt@comorment:/nrec/space$ ls
bayramc  lost+found  michealt  ofrei
michealt@comorment:/nrec/space$ cd michealt/
michealt@comorment:/nrec/space/michealt$ ^C
michealt@comorment:/nrec/space/michealt$ ls
github
michealt@comorment:/nrec/space/michealt$ cd github/
michealt@comorment:/nrec/space/michealt/github$ ls
BioPsyk
michealt@comorment:/nrec/space/michealt/github$ cd  BioPsyk/
michealt@comorment:/nrec/space/michealt/github/BioPsyk$ ls
cleansumstats
michealt@comorment:/nrec/space/michealt/github/BioPsyk$ 

```

Also using screen now to make sure I can save [[How to Use Linux Screen|Screen Sessions]]


## [[15.02.22]]
Sandeep made a bash script that should do what I want
``` bash
#! /bin/bash
# Job name:
#SBATCH - job-name=print files
#
# Project:
#SBATCH - - account=p33_norment
#SBATCH - - time=180:00:00
#SBATCH - - cpus-per-task=4

# Max memory usage:
#SBATCH - -mem-per-cpu=2000m
# specify the total number of files
#SBATCH - array 1-50

readarray -t FILES < files.txt
export filename=\$\{FILES [\$\{SLURM_ARRAY_TASK_ID\} ] $\}$
echo $\$$ filename
```
> this should work, but the only caveat is that you should run this script in a different directory other than the one with the filenames
> 
> otherwise it will keep looping infinitely (because of the slurm output produced will be read again and again continuously)
> 
> you can generate files.txt by using "ls > files.txt" in the folder that you want to read the files
``` bash
#!/bin/bash

#SBATCH - - ntasks=1
#SBATCH - - partition sixhour
#SBATCH - -time $=6: 00: \theta 0$
#SBATCH - - array=1-1000

LINE=\$(sed -n "\$SLURM_ARRAY_TASK_ID"p File.txt)
echo \$LINE

call-program-name-here \$LINE
```

ok this looks good except that I need a list of the meta data files. which I can get from the code that Oleks made. GO back and grab that. Actually just go ahead and write that whole thing out



## [[11.02.22]]
Lol didn’t get to it today instead did some reorganizing of the [[cleansumstats]] doc and review.
BUT, I did move some stuff to the durable folder (I think that may not be that folder actually)

My plan was to look at the data to get a better feel for it, but that didn’t happen.

One other thing was going over the [[cleansumstats definitions]] which is  alittle more theory study. 

I need to find that metadata he linked me to at some point there was a github describing the metadata, fuck where was that.
- It was in [[BioPsyk.cleansumstats.README#More documentation]] 
- That’s not entirely what I was thinking about there is definitely more




## [[10.02.22]]
Need to note, talking to Sandeep he mentioned that while you can not access thew cluster from the cluster file structure from the windows vm, the *durable* location is located on the M network drive. so you could move files there if you wanted to read them.

Fuck what was this lmao, like the actual directory:

> /cluster/projects/p697 isn’t available from Windows. 
> Copy files to home folder, /tsd/p697/home/p697-michaejt
>  or to /tsd/p697/data/durable/users/p697-michaejt
>   these two folders are  available on Windows machines
>  - Oleks



## [[08.02.22]]
So using: [[cleansumstats tasks#^egvhcf]] on the output file I found in my user directory resulted in a zero line output. There is nothing in there.

WHHAHHAHTHAHTTTT

You can’t export from the TSD

So create a list  using the BASH list function from above. See if you can add a recursive option



## [[07.02.22]]
Ran some SLURM jobs successfully but something went wrong on the output, in that it didn’t find the directories or create them so best I can tell it just dropped everything

Also trying to run the [python scrOLEK'S TEMPLATE CLEANSUMSTATS SLURM JOBipt](https://github.com/precimed/GWAS_SUMSTAT/blob/master/make_slurm.py) he made but to no avail. There were some things that did not match up directly to the server conditions. Such as the source directory

## [[04.02.22]]
Just get aslurm script to run a single css job

Looking at [[UiO HPC Job Script]]
Making [[UIO HPC Job Submit]]

`$SLURM_ARRAY_TASK_ID` is the env variable for the array number


## [[03.02.22]]
OK so extending the slurm script from below.
I think today I will focus on how cleansumstats works
But like what else could be left with the pseudo code?
``` pseudocode
$ARRAYno = 1 - size(Folder of multiple GWAS studies)
$InFolder = DirectoryList(Folder of multiple GWAS studies,$ARRAYno)
$OutFolder = OutputDirList($ARRAYno)

cleansumstats -i Folder (Or I guess it will be pointing to a meta data file, might be a problem if the name is different on each). If so I'll just make the pull list refer to the meta data files

I will change this so that it pulls from a premmade text file with the names of all the subdirectories


Also , premake an an output folder. Doesn't need to be versioned/dated at this time. 

Send the outputs from each processed input into their own subdirectory there. This can also be predone. and a list can be made from which the slurm job will pull.



```

Ok, need to add some sort of parallelization if possible.
Also going to need logs, make sure you add that to the SLurm job

Template that Oleks uses, apparently what he does is use a pythin script to create multiple templates and run them. See [https://github.com/precimed/GWAS_SUMSTAT/blob/master/make_slurm.py](https://github.com/precimed/GWAS_SUMSTAT/blob/master/make_slurm.py)  

This is the template he uses in python: ![[Olek's Template CleanSumStats SLURM job]]
This looks good but it’s missing a lot



### While we’re here let’s take a look at the cleansumstats metadata yaml schema description
I’ll make it a note: **raw-metadata.yaml**
Still reading it on the github though, easier
Skipped halfway through

## [[31.01.22]]
So having learned no lessons on keeping my work documented, I have not mentioned about where I left off with trying to run it but the putty terminal not sending or recognizing the newline breaks.

So I have since abandoned that and have resorted to just sending them inline, without the `\`
**This was due to there being a dangling space after the \ **


Running: 
```
cleansumstats/cleansumstats.sh \
-i SUMSTATv2_RAW/PGC_SCZ_2014_EUR/BGC_SCZ_2014_EUR.cleansumstats_meta 
-o out_example \
-d out_dbsnp \
-k out_1kgp 
```
Results in error `dpsnpdir doesn't exist`
Which probably means I’m missing something

The fix was to run it directly from the cleansumstats folder
OK so now it is running and taking a minute.

### Talked with Oleks about the cleansumstats.
```
GNU screen

kinit

cat
zcat - for compressed files - zcat, gunzip, .
less 

vi, nano, emacs - for editting
```

One of the things he did was pipe the files for reading such as the input files into word count / line count `wc -l` as well as head to read the top 10 lines and headers:
```
zcat cleaned GRCh38.gz | wc -l
zcat cleaned GRCh38.gz | head
```  

^egvhcf
he did this in the output folder `/out_example/`:
Resulting in an output like:

![](file:///home/Mike/Pictures/Screenshot_20220131_143536.png)


details folder of the output folder `/out_example/details/`
which contained the following:
```
genome_build_map_count_table_chrpos.txt 
removed_lines.gz
selected_source_stats.txt
genome_build_map_count_table_markername.txt
removed_lines_per_type_table.txt 
stepwise_overview.txt
```

Removed lines shows the number of lines removed and gives the reason why:
```
cat removed lines per type table.txt NrExcludedRows ExclusionReason

1103612 notPossPair
3898650 palin
399918 notGCTA
```

One of the examples he gave was:
a/t c/g - ambiguous SNPs

Also suggested looking at the SNPs:
rs112887542 - an identifier from NCSI dbSNP database

### Wrapping into SLURM
Pulling from the [hello.md ](https://github.com/comorment/containers/blob/main/docs/hello.md)on the[ Comorment-Containers Github](https://github.com/comorment/containers)
As well as the [TSD HPC guide here](https://www.uio.no/english/services/it/research/sensitive-data/help/hpc/colossus-userguide.html)

Basically I will need to set this up to process these files and flag me whenever an error occurs so that I can see what went wrong.
It sounds like I’m doing QA testing on the pipeline

**Slurm script**
> Run singularity container within SLURM job scheduler, by creating a `hello_slurm.sh` file (by adjusting the example below), and running `sbatch hello_slurm.sh`:
    
``` bash
#!/bin/bash
#SBATCH --job-name=hello
#SBATCH --account=p697
#SBATCH --time=00:10:00
#SBATCH --cpus-per-task=1
#SBATCH --mem-per-cpu=8000M
module load singularity/3.7.1
singularity exec --no-home hello.sif plink --help
singularity exec --home $PWD:/home hello.sif plink --bfile chr21 --freq --out chr21
```

I’m probably going to want this to run an array so something like:
``` pseudocode
$ARRAYno = 1 - size(Folder of multiple GWAS studies)
$InFolder = DirectoryList(Folder of multiple GWAS studies,$ARRAYno)
$OutFolder = OutputDirList($ARRAYno)

cleansumstats -i Folder (Or I guess it will be pointing to a meta data file, might be a problem if the name is different on each). If so I'll just make the pull list refer to the meta data files

I will change this so that it pulls from a premmade text file with the names of all the subdirectories


Also , premake an an output folder. Doesn't need to be versioned/dated at this time. 

Send the outputs from each processed input into their own subdirectory there. This can also be predone. and a list can be made from which the slurm job will pull.

```

## [Splitting a Job into Tasks (Array Jobs)](https://www.uio.no/english/services/it/research/sensitive-data/help/hpc/job-scripts.html)

To run many instances of the same job, use the --array switch to sbatch. This is useful if you have a lot of data-sets which you want to process in the same way with the same job-script:

`sbatch --array=_from_-_to_ [_other_ _sbatch switches_] _YourScript_`

You can also put the --array switch in an #SBATCH line inside the script. _from_ and _to_ are the first and last task number. Each instance of _YourScript_ can use the environment variable $SLURM_ARRAY_TASK_ID for selecting which data set to use, etc. For instance:

`sbatch --array=1-100 _MyScript_`

will run 100 copies of _MyScript_, setting the environment variable $SLURM_ARRAY_TASK_ID to 1, 2, ..., 100 in turn.

It is possible to specify the task ids in other ways than _from_-_to_: it can be a single number, a range (_from_-_to_), a range with a step size (_from_-_to_:_step_), or a comma separated list of these. Finally, adding _%max_ at the end of the specification puts a limit on how many tasks will be allowed to run at the same time. A couple of examples:

> Specification   Resulting TASK_IDs
> 1,4,42        # 1, 4, 42
> 1-5           # 1, 2, 3, 4, 5
> 0-10:2        # 0, 2, 4, 6, 8, 10
> 32,56,100-200 # 32, 56, 100, 101, 102, ..., 200
> 1-200%10      # 1, 2, ..., 200, but maximum 10 running at the same time

_Note_: spaces, decimal numbers or negative numbers are not allowed.

The instances of an array job are independent, they have their own $SCRATCH and are treated like separate jobs. (This means that they count against the limit of the total number of jobs a user can have in the job queue, currently 400.) You may also specify a parallel environment in array-jobs, so that each instance gets e.g. 8 processors. To cancel all tasks of an array job, cancel the jobid that is returned by the _sbatch_ command.

See man sbatch for details.

An extended example:

```
$ cat JobScript
#!/bin/bash
#SBATCH --account=_YourProject_
#SBATCH --time=1:0:0
#SBATCH --mem-per-cpu=1G
#SBATCH --array=1-200

module purge   # clear any inherited modules
set -o errexit # exit on errors

DATASET=dataset.$SLURM_ARRAY_TASK_ID
OUTFILE=result.$SLURM_ARRAY_TASK_ID

cp $DATASET $SCRATCH
cd $SCRATCH
chkfile $OUTFILE
_YourProgram_ $DATASET > $OUTFILE
```

`$ sbatch JobScript`

This job will process the datasets dataset.1, dataset.2, ... dataset.200 and leave the results in result.1, result.2, ... result.200.

### Working on the jobscript in the snippet txt
So I’ll probably just create the list of folders beforehand and tell it to iterate from that.
Just to reduce “on the fly ness”
Yeah create some text fil ahead of time and have the slurm job refer to that one

https://tldp.org/LDP/abs/html/varassignment.html
https://www.metagenomics.wiki/tools/ubuntu-linux/shell-loop

---
## [[28.01.22]]
Ok so now I rsynced the directory to me personal folder `\cluster\p697\users\michaejt\`
(Accidentally got the entire directory in my projects folder instead of putting it in its own subfolder. Will need to fix.)

I am still getting errors. Twofold, I think I am having first a permissions issue (even after rsyncing to my personal project folder), as it typically returns the following:

```
Failed to read/validate metadata file /cleansumstats/input: /cleansumstats/input (Is a directory) ~bash-4.23 ./cleansumstats.sh: line 44: [: ==: unary operator expected

~bash: ./cleansumstats.sh:: No such file or directory

~bash-4.23 ./cleansumstats.sh: line 48: [: ==: unary operator expected
```

and when I check on the folder itself 

```
-bash-4.2§ ./PGC_SCZ_2014_EUR/PGC_SCZ_2014_EUR.cleansumstats meta Bash: ./PGC SCZ 2013 EURJBGC. SCZ 2013 EUR.cleansumstats meta: Permission denied
```

Second the code 
``` ./cleansumstats.sh \  
-i /cluster/projects/p697/projects/SUMSTATv2_RAW/PGC_SCZ_2014_EUR/PGC_SCZ_2014_EUR.cleansumstats_meta \  
-o out_example \  
-e
```
Does not run as all on one “line”. Instead it runs piecemeal.
I did try running it as one line and it gave me something else.


![[Linux Quick Reference#mv]]



I keep getting `-bash: !: event not found` when trying to do this command, because I had not used the above command
    

### So I am using
`mv !(cleansumstats|SUMSTATv2_RAW) SUMSTATv2_RAW`
finally worked

## [[27.01.22]]
rsynced the folders with my personal one

`rsync -avP cluster/projects/p697/projects/cleansumstats /cluster/projects/p697/users/michaejt`

Ran the demo code
```
# iv. clean a sumstat using shrinked example data for dbsnp and 1kgp (-e flag)  
./cleansumstats.sh \  
-i tests/example_data/sumstat_1/sumstat_1_raw_meta.txt \  
-o out_example \  
-e
``` 

Now doing it for real data:
`/cluster/projects/p697/projects/SUMSTATv2_RAW/PGC_SCZ_2014_EUR/PGC_SCZ_2014_EUR.cleansumstats_meta`

so 
``` 
./cleansumstats.sh \  
-i /cluster/projects/p697/projects/SUMSTATv2_RAW/PGC_SCZ_2014_EUR/PGC_SCZ_2014_EUR.cleansumstats_meta \  
-o out_example \  
-e
``` 

Ok so it’s a directory that is output, or better phrased the output is sent to a new directory which contains the following files
![](file:///home/Mike/Pictures/Screenshot_20220127_154355.png)

What we get is the following out 
> Add output files here

Now I’m not sure what I’m even looking at
There are several different files and types. Some of them are zipped, several are binary and in their own folders
need to document what they are

Maybe I can look at the input files and see how that differs?

It looks like I can’t access the original file `/cluster/projects/p697/projects/SUMSTATv2_RAW/PGC_SCZ_2014_EUR/PGC_SCZ_2014_EUR.cleansumstats_meta` so I’m trying to rsync it to my folder and maybe I can be granted read access from there

Getting this on output:
```  shell

Failed to read/validate metadata file /cleansumstats/input: /cleansumstats/input (Is a directory) ~bash-4.23 ./cleansumstats.sh: line 44: [: ==: unary operator expected

  

~bash: ./cleansumstats.sh:: No such file or directory

  

~bash-4.23 ./cleansumstats.sh: line 48: [: ==: unary operator expected

  

bash: ./cleansumstats.sh:: No such file or directory
```



