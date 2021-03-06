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

export CLEANSUMSTATS=/cluster/projects/p697/projects/cleansumstats
export RAW=/cluster/projects/p697/projects/SUMSTATv2_RAW
export OUT=/cluster/projects/p697/projects/SUMSTATv2_dev

cd ${{CLEANSUMSTATS}} && ./cleansumstats.sh 
-i ${{RAW}}/{sourcedir}/{id}.cleansumstats_meta 
-d out_dbsnp 
-k out_1kgp 
-o ${{OUT}}/cleansumstats

cd ${{OUT}}/cleansumstats/{id}/ && paste <(zcat cleaned_GRCh37.gz) <(cut -f 5- <(zcat cleaned_GRCh38.gz) ) | gzip > cleaned_GRCh37.sumstats.gz

```