# Using cleansumstats
## What is cleansumstats?
Cleansumstats is a tool developed by our collaborator [Jesper R. Gådin](https://github.com/pappewaio) to *“Convert GWAS sumstat files into a common format with a common reference for positions, rsids and effect alleles”.*

For more information about the tool itself check out the readme in the repo (might need permissions before you can access this) https://github.com/BioPsyk/cleansumstats

**We are using cleansumstats to standardize / harmonize data from the variety of sumstat formats we obtain.**
For more information about sumstats see the wiki page: https://wiki.norment.uiocloud.no/dokuwiki/where_to_find_summary_stats

**For reasons of brevity I will refer to cleansumstats by its acronym CSS or css**, which is not to be confused with *Cascading Style Sheets*; which will absolutely never come into any context found here.

## How do we use it?
For the developer directions check out the repo readme here [[BioPsyk.cleansumstats.README|the repo readme here]]. However the way we will use it in our system is a little different.

### A Simple css script
This is a bash shell script, which can be run in a terminal line by line. Alternatively this can be saved as file somewhere and be run in terminal via the file name. The example below has to be run while your working directory is your personal sandbox folder.
```shell
module load singularity/3.7.1

cd /cleansumstats

./cleansumstats.sh \
-i SUMSTATv2_RAW/IPDGC_PD_2018/IPDGC_PD_2018.cleansumstats_meta \
-o SUMSTAT_OUT \
-d out_dbsnp \
-k out_1kgp 
```

The first line `module load singularity/3.7.1` loads the singularity container in which css is run.

The second block of code, runs as a single “line” of code where `\` means that each line is a continuation of the previous one. This is because the first line  `cleansumstats.sh` should point at the copy of cleansumstats you want to run, while the following lines are the input options.

`-i` is the input. Put here the path to the file you want to input into css.
`-d` and `-k` point to reference files in the css repo. These will not change, just make sure the path points to the `out_dbsnp` and`out_1kgp` files in the css repo. 
`-o` is the output folder for the standardized out folders. You can pretty much direct this anywhere, though in this example I have created a `SUMSTAT_OUT` folder in my sandbox directory.

For more information on css input options see [[CleanSumStats Developer instructions]]

---
### Same script but with the paths spelled out
While the example above assumes your working path is already set to your sandbox directory, the example immediately below can be run from anywhere. If you just swap out the username in the below code block, you should be able to basically just copy and paste to run it (assuming you’ve created all the prerequisite folders. See [[03 Creating a personal sandbox folder on cluster]]).

```shell
module load singularity/3.7.1

/cluster/projects/p697/users/michaejt/cleansumstats/cleansumstats.sh \
-i /cluster/projects/p697/projects/IPDGC_PD_2018/IPDGC_PD_2018.cleansumstats_meta \ 
-d /cluster/projects/p697/users/michaejt/cleansumstats/out_dbsnp \ 
-k /cluster/projects/p697/users/michaejt/cleansumstats/out_1kgp \
-o cluster/projects/p697/users/michaejt/SUMSTAT_OUT
```

Also note this example takes an input directly from the regular SUMSTATSv2_RAW folder.

## Running as a SLURM job
For further information see [[05 Running CleanSumStats as a SLURM job]]
But here is a quick example Slurm job you can run. I will not cover how to use slurm. Directions on how to use slurm can be found here: [[UIO HPC Job Submit]] and here: [[UiO HPCJob Script]].

Once you are ssh-ed into the cluster you can submit a bash script as a job to run on the cluster machine. Just save the below as a file in your working directory and submit it. 

Before you do though, be sure to change `<directory of sumstat>` and `<sumstat meta file name>` to the names of the folder and meta data file you want to run. 
E.g.:
``` shell
export sourcedir=IPDGC_PD_2018
export metaid=IPDGC_PD_2018
```

Note that here the `metaid` is the *name* of the metadata file, but not the complete filename including the file extension `*.cleansumstats_meta`, which is added later in the job script.


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

$SCRATCH && module load singularity/3.7.1

export CLEANSUMSTATS=/cluster/projects/p697/projects/cleansumstats
export RAW=/cluster/projects/p697/projects/SUMSTATv2_RAW
export OUT=/cluster/projects/p697/users/michaejt/SUMSTATv2_OUT
export sourcedir=<directory of sumstat>
export metaid=<sumstat meta file name>

cd $CLEANSUMSTATS} && ./cleansumstats.sh 
-i ${RAW}/${sourcedir}/${metaid}.cleansumstats_meta
-d out_dbsnp 
-k out_1kgp 
-o ${OUT}/cleansumstats

cd ${OUT}/cleansumstats/${metaid}/ && paste <(zcat cleaned_GRCh37.gz) <(cut -f 5- <(zcat cleaned_GRCh38.gz) ) | gzip > cleaned_GRCh37.sumstats.gz

```

You may have noticed this uses the CSS repo and input files as found in the project folder as opposed to your own sandbox versions. This is done to make the above as easily copy-and-paste-able for any case. You may go ahead and change them to point at your sandboxed versions as you like, and in the case of troubleshooting this will be necessary.