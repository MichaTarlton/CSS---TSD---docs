# Running CleanSumStats as a SLURM job

[[Olek's Template CleanSumStats SLURM job]]
[[UiO HPC Job Script]]
[[UIO HPC Job Submit]]
[[Example SLURM log file]]

## Dissecting the simple slurm job
[[04 Using cleansumstats#Running as a SLURM job|In the previous section]] we gave a simple example slurm job.
Here we will explain in depth more about how css works as a slurm job.
Starting with the simple example given in the previous section.

``` shell
#!/bin/bash
#SBATCH --job-name=SUMSTAT
#SBATCH --account=p697_norment
#SBATCH --time=4:00:00
#SBATCH --ntasks=1
#SBATCH --mem-per-cpu=8000M
#SBATCH --cpus-per-task=16

source /cluster/bin/jobsetup

set -o errexit

$SCRATCH && module load singularity/3.7.1

export CLEANSUMSTATS=/cluster/projects/p697/projects/cleansumstats
export RAW=/cluster/projects/p697/projects/SUMSTATv2_RAW
export OUT=/cluster/projects/p697/users/michaejt/SUMSTATv2_OUT
export sourcedir=<directory of sumstat>
export metaid=<sumstat meta filename>

cd ${CLEANSUMSTATS} && ./cleansumstats.sh \
-i ${RAW}/${sourcedir}/${metaid}.cleansumstats_meta \
-d out_dbsnp \
-k out_1kgp \
-o ${OUT}/cleansumstats

cd ${OUT}/cleansumstats/${metaid}/ && paste <(zcat cleaned_GRCh37.gz) <(cut -f 5- <(zcat cleaned_GRCh38.gz) ) | gzip > cleaned_GRCh37.sumstats.gz
```

### Slurm Header information
Quickly explaining the slurm specific parts of this example.
```
#!/bin/bash
#SBATCH --job-name=SUMSTAT
#SBATCH --account=p697_norment
#SBATCH --time=4:00:00
#SBATCH --ntasks=1
#SBATCH --mem-per-cpu=8000M
#SBATCH --cpus-per-task=16
```
This is the header information which tell the HPC how to run the job and with what hardware. There is no need to change any of this and recommend you don’t. `--job-name` however can be changed to whatever name you like.

### source and set 
These two commands you do not need to change, but you can move them around if you need to for clarity in job script. I set them towards the bottom in the more advanced examples below.

`source` is the [bash source command](https://linuxize.com/post/bash-source-command/) which I’ll be honest I’m not entirely certain what it does here. I believe it creates a space on the cluster in which to operate the job.

`set -o errexit` exits the script upon hitting an error.

### Singularity
The line `module load singularity/3.7.1` loads the singularity container in which css is run.
**ADD NFO ABOUT THE TESST SCRATCH**

### Variables
In this part we define the variables we use in the job such as paths for the CSS program, input directory and files, and other.
The `export` command just ensures that these variables are global across the instance they are declared for.

```shell
export CLEANSUMSTATS=/cluster/projects/p697/projects/cleansumstats
export RAW=/cluster/projects/p697/projects/SUMSTATv2_RAW
export OUT=/cluster/projects/p697/users/michaejt/SUMSTATv2_OUT
export sourcedir=<directory of sumstat>
export metaid=<sumstat meta filename>
```
In this example, we use the “live” copy of cleansumstats, as well as the “RAW” input files from the projects directory. We however output to our own sandbox directory as we do not want to disrupt the active cleaned susmtats.

The `sourcedir` and the `metaid` respectively are: the folder name where the sumstat files are located, and the specific sumstat metadata file you want to run.

**Note:** that here the `metaid` is the *name* of the metadata file, but not the complete filename including the file extension `*.cleansumstats_meta`, which is added later in the job script. The reasons for doing is we use the metadata name independently as you will see in following examples.


### cleansumstats
This portion is largely unchanged from how [[04 Using cleansumstats|I have described it in the previous section]], only with our variables slotted in. I will talk more about additional troubleshooting options later on.

We do however have an additional portion at the bottom here:
``` shell
cd ${OUT}/cleansumstats/${metaid}/ && paste <(zcat cleaned_GRCh37.gz) <(cut -f 5- <(zcat cleaned_GRCh38.gz) ) | gzip > cleaned_GRCh37.sumstats.gz
```
This part performs a post-run modification where the output files are split. This cuts part from the output `cleaned_GRCh38.gz` and attaches it to the `cleaned_GRCh37.gz` file. **ASK OLEKS TO REMIND YOU EXACTLY WHY.** Leaving us with our desired output file `cleaned_GRCh37.sumstats.gz`.

### Log files – Reading the output
Your slurm job should create an output log in the working directory you submitted the job from, which should have a filename like `slurm-13695820_33.out`. In this example, 13695820 was the job number the scheduling service gave to our submission, and 33 was the array number. This is primarily useful for troubleshooting. See [[Example SLURM log file]].

In the case you are running an array of jobs. Each job will create a log file with the array number appended to the end (as above). There is an option to define the output folder for slurm logs, but I have forgotten what that is at this time. You can even get fancy with it and create different folders for each job number.

## Running multiple css jobs
Until now we have shown how to run a single sumstat job, cleaning a *single* sumstat file. As of [current inventory count](https://docs.google.com/spreadsheets/d/19cURugXQQyLgfLU-gwCReuWK99DcpODOpSyDkaR-bow/edit#gid=1515118726) there are 277 different sumstats available for processing and more to be added in the future. A quick list of all available metadata files returns about 362 hits.

### Python Solution
The previous solution to this was developed by Oleks is a python script which takes the template for a css slurm job, and creates a job script for each `*.cleansumstats_meta*` file it finds.

This can be found in the [GWAS_SUMSTATS repo](https://github.com/precimed/GWAS_SUMSTAT/blob/master/make_slurm.py) or the local copy here: [[make_slurm.py]].

The drawback to this is each job script must be submitted manually.

### Slurm array solution
Using slurm’s `--array` feature we can direct the job script to draw the file paths and sumstat file names we want to run from an external list and then it will automatically create a job for each.

The form this takes in the slurm job script header is `#SBATCH --array=`,
where we can have it select from a range `#SBATCH --array=1-100` or select a particular set `#SBATCH --array=2,54,33,35,92,96,98`.

We can then set a variable in our bash script to be the number specified from the array by `NUM=$SLURM_ARRAY_TASK_ID` where I have named the variable `NUM`.

**[[06 Creating lists of metadata files and filepaths|I HAVE MADE A GUIDE ON HOW TO CREATE A LIST OF METADATA FILES AND FILE PATHS HERE]]**

### Example Slurm array job script
Below is an example slurm job script for multiple files.
I have included comments under each command to summarize its function.
This should be directly copy-and-past-able, though I would suggest modifying the array range to not create 50 jobs all at once.

``` bash 
#!/bin/bash
#SBATCH --job-name=SUMSTAT
#SBATCH --account=p697_norment
#SBATCH --time=4:00:00
#SBATCH --ntasks=1
#SBATCH --mem-per-cpu=8000M
#SBATCH --cpus-per-task=16
#SBATCH --array=1-50


NUM=$SLURM_ARRAY_TASK_ID 
## set the array number to the variable $NUM
## Slurm already creates the variable $SLURM_ARRAY_TASK_ID , but I'm using $NUM instead for ease

echo ${NUM}  
## Repeats the array number back to us. Viewable in the output log. Useful for troubleshooting


## The next few lines creates variables that later plug into the css input options. Easier to modify them here, or even save multipl options and just comment out (anything behind ## on a single line) whatever you are not using at a given time

export CLEANSUMSTATS=/cluster/projects/p697/projects/cleansumstats 
## Path for the cleansumstats tool 

export RAW=/cluster/projects/p697/projects/SUMSTATv2_RAW
## Path for the input sumstats folder

export OUT=/cluster/projects/p697/users/michaejt/SUMSTATv2_OUT
## Path for our desired output folder

export LIST=/tsd/p697/data/durable/users/michaejt/lists/metalist_woutfolders2.txt
## Path to the list of metadata file names (minus their file extension)
## I have proivded the list I have already made in this example


export listname=$(sed "${NUM}q;d" ${LIST})
## selects the metadata filename from the provided list


export PLACE=$(find ${RAW} -type f | grep -E ${listname}.*cleansumstats_meta)
## creates the full filepath for the metadata file


source /cluster/bin/jobsetup

set -o errexit

test $SCRATCH && module load singularity/3.7.1 
## loads the singularity container for 

cd ${CLEANSUMSTATS} && ./cleansumstats.sh \
-i ${PLACE} \
-d /cluster/projects/p697/users/michaejt/cleansumstats/out_dbsnp \
-k /cluster/projects/p697/users/michaejt/cleansumstats/out_1kgp \
-o ${OUT}/cleansumstats/${listname} \
-w $SCRATCH/work

cd ${OUT}/cleansumstats/${listname}/ && paste <(zcat cleaned_GRCh37.gz) <(cut -f 5- <(zcat cleaned_GRCh38.gz) ) | gzip > cleaned_GRCh37.sumstats.gz
```

Uhhh, I could probably expand on this. However for the moment I will move on to something else let me know if you have questions.