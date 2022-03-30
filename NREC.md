# NREC

The NREC is a sandbox server for testing and importing software and data to the TSD [citation needed].

## Accessing NREC
### Permissions
First, you will need to ask ask Sandeep to add you as a user to the NREC user list. 

### SSH-ing to NREC
Once you have been assigned a user on the NREC machine, you will be able to SSH to it from any terminal (no need to use VMware). So from your own computer connect to NREC with your username via:
```
ssh michealjt@158.39.200.231
```

or in my case just 

```
ssh nrec
```

See [[Linux Quick Reference#SSH]] for more information on making connecting via SSH easier.

Also if necessary see if you require access to the NREC dashboard.

### Create a personal sandbox directory
If you have the permissions, create a personal directory on NREC under `/nrec/space`
E.g.: `/nrec/space/michealt`

## Importing a new version of CSS to NREC (and eventually TSD)
A primary use case of utilizing the NREC machine is pulling a new version of CSS [from the developer repo](https://github.com/BioPsyk/cleansumstats) and preparing it for transfer over to the TSD.

This will require a functioning knowledge of git, which I will not expand on here, but might include in the [[00 CSS cheat sheet#Git]].

Create a new folder for your repositories in your personal folder, e.g.: `/nrec/space/michealt/github/` and use git to clone the developer repo to your NREC folder.

#### Testing
After cloning the new css repo, test setting it up and running it on NREC following the [[BioPsyk.cleansumstats.README#Quick Start|developer instructions]]. This includes ensuring the singularity container is current or compatible with the new version of css.

### Note on the dbsnp and 1kgp files
You may have noticed the developer instructions for running a quick test include using a shrinked version of the dbsnp and 1kgp reference files. This is because these are extremely large files which do not change between versions of CSS. In interest of brevity we would prefer to not download or move new copies.

Instead, when moving to a new version of CSS, we will prefer to move copies of these files from the old version of CSS into the new version. 
 This includes the files:
out_dbsnp
out_1kgp

### Deploying new versions of CSS
Oleks deployed it I think. I need to figure out how to use the TSD API to deploy it.
Actually we may have used the regular TSD import option.
See [[08 Importing and Exporting Data with TSD]]


## Setting up Python environment on NREC
See [[08 Importing and Exporting Data with TSD]]
We be using miniconda here boys
Followed directions above
[[tsd-s3cmd --guide]]
Created `home/michaelt/.config` folder according to directions and created a .s3cfg file there according to guide.
Also had to install libsodium from scratch as dependencies appeared to be gone

```
Your TSD project's access and secret key can be found in:
    /tsd/pXX/data/durable/s3-api-access-keys.
```

Failing with s3mcd at `tsd-s3cmd mb s3://mybucket`
Moving over to TACL as Sandeep says it’s the new one
Appears to already be installed as well


S3CMD

**ARE WE USING TACL OR TSD-s3cmd?**
TACL is the new one, looks like it allows remote syncing

**BOTH** -Oleks


## TACL
Input appears to be of the sort
```
tacl p697 --option
```

See [[TACL --help]]
See [[tacl --guide uploads]]