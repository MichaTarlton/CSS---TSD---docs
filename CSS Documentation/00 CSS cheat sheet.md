# CleanSumStats cheat sheet
## Repos
### https://github.com/BioPsyk/cleansumstats
**The tool repo** 
- As maintained with our collaborator Jesper Gådin
- [[BioPsyk.cleansumstats.README]]
- [[CleanSumStats Developer instructions]]

### https://github.com/precimed/GWAS_SUMSTAT/
**Repo containing meta-data associated with MMIL-OSLO inventory of summary statistics:** 
- Save to your personal machine at `/home/Mike/github/precimed/GWAS_SUMSTAT/`
- See the [[precimed.GWAS_SUMSTAT.README|README]]
- Contains make_slurm.py’
- Using it to modify and maintain live metadata 

### https://github.com/precimed/GWAS_SUMSTAT/tree/master/cleansumstats_meta
**Same as above repo, but specifically where we keep and maintain our metadata files**
- Explained elsewhere
- **INSERT**

## Working Directories and SSH addresses
Because I keep needing an easy copy/paste

### TSD and appnodes
Appnode ssh address - the ones in the wiki are wrong:
`p697-appn-norment01`
or to be more specific
`ssh p697-michaejt@p697-appn-norment01`

“live” sumstat project folders
`/cluster/projects/p697/projects/SUMSTATv2_dev/`

`/cluster/projects/p697/projects/SUMSTATv2_RAW/`

 Personal cluster folder
`/cluster/projects/p697/users/michaejt/` 

Personal home folder - easier to access from file explorer
`/tsd/p697/home/p697-michaejt/p697code/` 

**Import:**  
	Win: `N:\durable\file-import`  
	Shell: `/tsd/p697/data/durable/file-import`  
**Export:**  
	Win: `N:\durable\file-export`  
	Shell: `/tsd/p697/data/durable/file-export`
	
### NREC
NREC SSH address
`ssh michealt@158.39.200.231`

NREC user dir: `michealt@comorment:/nrec/space/michealt/github/BioPsyk/cleansumstats`

#### NREC API ACCESSS
Username: 'michaejt@uio.no'
Password: '8XscCg0wLR0LB4Po'


## Sumstats Inventory catalog
https://docs.google.com/spreadsheets/d/19cURugXQQyLgfLU-gwCReuWK99DcpODOpSyDkaR-bow/edit#gid=1515118726
- Catalog maintained by Nadine

## slurm
`sbatch jobscript`
- submit job script with filename `jobscript`

`squeue`
- see current job queue on cluster
- add `-j <job number>` to see only the job number (and its arrays) specified
- 

`qsumm` 
- queue summary
- Can be used to see which accounts are most available before running your job

## LINUX
See [[Linux Quick Reference]] 

## Git

## Python

## Common problems and how to work around them
![[01 Accessing TSD through VMWARE HORIZON#Copying and pasting into the VMware session]]


