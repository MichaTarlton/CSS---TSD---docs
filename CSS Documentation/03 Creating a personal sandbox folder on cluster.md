# Creating a personal sandbox folder on cluster

### Create a personal folder
First create a personal folder in the users directory of the cluster:
`mkdir \cluster\p697\users\michaejt\`
- mkdir : create new directory

I’ll be referring to this folder as your “sandbox” or personal directory from here out. 


## Create a copy of the cleansumstats repo in your personal folder

``` bash
rsync -avP --exclude={'tmp'} /cluster/projects/p697/projects/cleansumstats/
/cluster/projects/p697/users/michaejt/
```
- rsync creates a sync between your target directory and the one you want to copy
- this should be one way, i.e. you can make changes to your copy without it changing anything in the original files
- be certain to use the option `-avP` or it might not work correctly
- This also excludes the sometime extremely large files `'out_dbsnp','out_1kgp','tmp'`
- However you will need `'out_dbsnp','out_1kgp'` so go ahead and see if you can sync them
- If you can’t, no worries, just run cleansumstats from the cluster repo

Go ahead and create a copy of the `/cluster/projects/p697/projects/SUMSTATv2_RAW/` folder while you are at it. This is large and may take awhile

There is no reason to copy the `/cluster/projects/p697/projects/SUMSTATv2_dev/` folders. Instead, direct output from your css runs to a folder in your personal folder. E.g.  `/cluster/projects/p697/users/michaejt/SUMSTAT_OUT`

## Alternative
Exclude the large 'out_dbsnp' and 'out_1kgp' files so that the repo copies faster.
**However,** this means when running the cleansumstats script you will need to specify the location (`/cluster/projects/p697/projects/cleansumstats/`) of these files as they will not be located in your snadbox repo.

``` bash
rsync -avP --exclude={'out_dbsnp','out_1kgp','tmp'} /cluster/projects/p697/projects/cleansumstats/ /cluster/projects/p697/users/michaejt/
```