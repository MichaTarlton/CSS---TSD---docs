# make_slurm.py
``` python
#module load Python/3.7.4-GCCcore-8.3.0
#source /cluster/projects/p697/ofrei/py3/bin/activate

import pandas as pd
import itertools
import numpy as np
import sys
import os
import glob

template="""#!/bin/bash
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

cd ${{CLEANSUMSTATS}} && ./cleansumstats.sh -i ${{RAW}}/{sourcedir}/{id}.cleansumstats_meta -d out_dbsnp -k out_1kgp  -o ${{OUT}}/cleansumstats
cd ${{OUT}}/cleansumstats/{id}/ && paste <(zcat cleaned_GRCh37.gz)  <(cut -f 5- <(zcat cleaned_GRCh38.gz) ) | gzip > cleaned_GRCh37.sumstats.gz
"""

if __name__ == "__main__":
    root_folder = 'cleansumstats_meta'
    files = glob.glob('{}/**/*.cleansumstats_meta'.format(root_folder), recursive=True)    
    files = [f.replace('{}/'.format(root_folder), '') for f in files]

    for file in files:
        with open('SUMSTAT.job', 'w') as f:
            sourcedir = os.path.dirname(file)
            id = os.path.splitext(os.path.basename(file))[0]
            f.write(template.format(id=id, sourcedir=sourcedir))
        if False:
            os.system('sbatch SUMSTAT.job')
```
