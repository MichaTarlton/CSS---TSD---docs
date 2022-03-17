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

**Note:** In this job we use the variable automatically created by slurm to refer to its own scratch directory `$SCRATCH`. Later on in the job script we instruct slurm to copy the temporary file to a different directory where we can review the output: 
`cp -r $SCRATCH/work /cluster/projects/p697/users/michaejt/scratch_out/${id}` 

