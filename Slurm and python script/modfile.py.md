# modfile.py
Explained in [[7.2 The state of troubleshooting as I leave it now#Routine preprocessing of the susmtats files]]
See also [[SLURMPY4.JOB]] which is the slurm job script which calls to this 
The actual copy of this is in my login node working folder copy under `production_scripts`
```python

## put this into a script which is called to 
import pandas as pd
import yaml

import sys ## for passing bash variables into python
import os

PLACE=sys.argv[1]
FLYDIR=sys.argv[2]
METADIR=sys.argv[3]

with open(PLACE, 'r') as stream:
    metadata = yaml.safe_load(stream)
    fname = metadata["path_sumStats"] ##Name of the sumstats file
    print(fname)
    ## fname = "${sumstat_file}" ## only used with the sed strategy on line 43. Deprecate candidate

inpath=os.path.join(METADIR,fname)
print(inpath)
outpath=os.path.join(FLYDIR,fname)
print(outpath)


df = pd.read_csv(inpath, delim_whitespace=True, dtype=str) ## hoping that by cd on line 52 we don't have to specify the name any further
df.head()
df.columns = df.columns.str.strip()
df.to_csv(outpath, sep='\t', index=False) ## In theory this writes it straight back to our fly file
## and then... that's it? I think. Move to testing.
## exit() opyhton doesn't work like this
print("done!")
```