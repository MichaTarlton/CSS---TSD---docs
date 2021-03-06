# SLURMPY4.JOB

Explained in [[7.2 The state of troubleshooting as I leave it now#Routine preprocessing of the susmtats files]]
See also [[mODfile.py]] which is the python script this calls to 
The actual copy of this is in my login node working folder copy under `production_scripts`

``` shell
#!/bin/bash
#SBATCH --job-name=SUMSTAT
#SBATCH --account=p697_norment
#SBATCH --time=4:00:00
#SBATCH --ntasks=1
#SBATCH --mem-per-cpu=8000M
#SBATCH --cpus-per-task=16
#SBATCH --array=92 ##52,54,93,42,39,58,57,56,55,51,50,49,53,87,79,88,91


NUM=$SLURM_ARRAY_TASK_ID
echo ${NUM}

export CLEANSUMSTATS=/cluster/projects/p697/projects/cleansumstats
export RAW=/cluster/projects/p697/projects/SUMSTATv2_RAW

export OUT=/cluster/projects/p697/users/michaejt/SUMSTATv3_OUT
export LIST=/cluster/projects/p697/users/michaejt/lists/uncleanedlist.txt

export id=$(sed "${NUM}q;d" ${LIST})
echo ${id}
## returns the metadata filename (WITHOUT file extension)

export PLACE=$(find ${RAW} -type f | grep -E ${id}.cleansumstats_meta)
echo ${PLACE}
## Here this returns the FULL path and filename with extension for the metadata file

##mkdir ${OUT}/cleansumstats/${id} ## In theory I don\t need this ## for the array test its just in case
##mkdir /tsd/p697/home/p697-michaejt/p697code/scratch/${id}
##mkdir -p /cluster/projects/p697/users/michaejt/slurpyjobtest/scratch/${id} ##mkdir -p creates all the folders in the path as needed

## make a location to copy the py scratch work to
mkdir ${SCRATCH}/fly
export flydir=${SCRATCH}/fly
echo $flydir
## place to copy the input files to 
## I really do not want to have to parse the metadata file for the specific file so I'm just copying the full dir

export metafile_dir=$(dirname "${PLACE}")
export metafile_name=$(basename "${PLACE}")
echo $metafile_dir
echo $metafile_name

cp $PLACE $flydir ## copy metadata
cd $flydir ##change directory to our on the fly location that should have both things

pyscripts=/cluster/projects/p697/users/michaejt/pyscripts ## Location of pyhton scripts that are to be run

module load Python/3.9.5-GCCcore-10.3.0
pip3 install pandas
pip3 install pyyaml

python $pyscripts/modfile.py ${PLACE} ${flydir} ${metafile_dir} ## Replace $SLURM_SUBMIT_DIR/ with a more permanan solution moving forward
##VARIABLE=`python $SLURM_SUBMIT_DIR/modfile.py ${PLACE} ${flydir} ${metafile_dir}`
##echo $VARIABLE
##cleanup "cp -r $SCRATCH/work /cluster/projects/p697/user/p697-michaejt/scratch/${id}"
## Honestly not certain if this did anything
## IIRC 'cleanup' is a slurm command to run something after the job has been completed
## Here I have it set to copy the scratch to a place I have easy access
## not really needed with the current -w command


source /cluster/bin/jobsetup

set -o errexit

test $SCRATCH && module load singularity/3.7.1 ## this modification is for slurm only
##module load singularity/3.7.1  ## for running piecemeal

cd ${CLEANSUMSTATS} && ./cleansumstats.sh \
-i ${flydir}/${metafile_name}  \
-d /cluster/projects/p697/users/michaejt/cleansumstats/out_dbsnp \
-k /cluster/projects/p697/users/michaejt/cleansumstats/out_1kgp \
-o ${OUT}/${id} \
-w $SCRATCH/work

##-i ${PLACE}  \

### ---

## not in original(taken out of make_slurm.py)
##export sourcedir=SSGAC_RISK_2019
##export id=SSGAC_RISK_2019
##
##export sourcedir=IPDGC_PD_2018
##export id=IPDGC_PD_2018
##
####export sourcedir=GIANT_HEIGHT_2018_UKB
####export id=GIANT_HEIGHT_2018_UKB
##
##cd ${CLEANSUMSTATS} && ./cleansumstats.sh \
##-i ${RAW}/${sourcedir}/${id}.cleansumstats_meta \
##-d /cluster/projects/p697/users/michaejt/cleansumstats/out_dbsnp \
##-k /cluster/projects/p697/users/michaejt/cleansumstats/out_1kgp \
##-o ${OUT}/cleansumstats/${id}
##
cp -r $SCRATCH/work /tsd/p697/home/p697-michaejt/p697code/scratch/${id}


cd ${OUT}/${id}/ && paste <(zcat cleaned_GRCh37.gz) <(cut -f 5- <(zcat cleaned_GRCh38.gz) ) | gzip > cleaned_GRCh37.sumstats.gz


```