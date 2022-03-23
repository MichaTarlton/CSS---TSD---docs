# cleansumstas slurm job template 10.03.22

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

export LIST=/tsd/p697/home/p697-michaejt/p697code/Lists/metalist_woutfolders2.txt
## Path to the list of metadata file names (minus their file extension)
## I have proivded the list I have already made in this example


export listname=$(sed "${NUM}q;d" ${LIST})
## selects the metadata filename from the provided list

echo ${listname}


export PLACE=$(find ${RAW} -type f | grep -E ${listname}.*cleansumstats_meta)
echo ${PLACE}


mkdir ${OUT}/cleansumstats/${listname} 
## In theory this is unecessary, as css should make this folder
## but making it here just in case

mkdir /tsd/p697/home/p697-michaejt/p697code/scratch/${listname}
## for troubleshooting

##cleanup "cp -r $SCRATCH/work /cluster/projects/p697/user/p697-michaejt/scratch/${id}"
## also unecessary with css -w option



source /cluster/bin/jobsetup

set -o errexit

test $SCRATCH && module load singularity/3.7.1 
## this modification is for slurm only
##module load singularity/3.7.1  ## use this instead when running piecemeal

cd ${CLEANSUMSTATS} && ./cleansumstats.sh \
-i ${PLACE} \
-d /cluster/projects/p697/users/michaejt/cleansumstats/out_dbsnp \
-k /cluster/projects/p697/users/michaejt/cleansumstats/out_1kgp \
-o ${OUT}/cleansumstats/${listname} \
-w $SCRATCH/work

### ---

cp -r $SCRATCH/work /tsd/p697/home/p697-michaejt/p697code/scratch/${listname}
## copies the scratch directory to my folder where I can look at it
## pretty sure this doesn't work as it's off cluster storage lol
## though it did make something there


cd ${OUT}/cleansumstats/${listname}/ && paste <(zcat cleaned_GRCh37.gz) <(cut -f 5- <(zcat cleaned_GRCh38.gz) ) | gzip > cleaned_GRCh37.sumstats.gz


```