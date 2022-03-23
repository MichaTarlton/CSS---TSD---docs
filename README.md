# So You Want to Run CleanSumStats
This repository is mostly written in github flavored markdown and can be viewed in any text editor, but in order to be properly viewed, it should be opened as a vault in the app [Obsidian](https://obsidian.md); where it can be navigated like a wiki.

The double brackets: [[example]] specify a link to another file located within the repository.

##  [[00 CSS cheat sheet]]
- put quick reference for css thing here
- Like working directories
- Linux commands
- Common issues I run into

## [[01 Accessing TSD through VMWARE HORIZON]]

## [[02 sumstat directory structure and files]]
- Main directories which will be used with CSS

## [[03 Creating a personal sandbox folder on cluster]]
- For testing

## [[04 Using cleansumstats]]

## [[05 Running CleanSumStats as a SLURM job]]

## [[06 Creating lists of metadata files and filepaths]]

## 07 Troubleshooting failed css runs
- In progress

## [[08 Importing and Exporting Data with TSD]]
- API section needs work
- Consider combining with NREC

## [[NREC]]
- Sandbox for TSD 
- Also where you can import things to TSD via API
- Importing new versions of CSS

## GWAS_SUMSTAT
- https://github.com/precimed/GWAS_SUMSTAT
- repository of meta-data associated with MMIL-OSLO inventory of summary statistics
- contains make_slurm.py’
- Talk about using it to modify and maintain live metadata 

## Python on TSD 
[[Using Python on TSD]]
Not really done better. pretty much the same actually.
**Include https://github.com/comorment/containers on how to use py using the containers**

## Importing New Sumstats to TSD
- Do with Nadine and Oleks
- Nadine only moves the new files to the RAW folder
	- She does not create metadata
	- Apparently we are the ones who do that
	- Probably using a python script in the GWAS_SUMSTAT
- How to create metadata
	- Do not include `#
- Sumstats Inventory Catalog
	- https://docs.google.com/spreadsheets/d/19cURugXQQyLgfLU-gwCReuWK99DcpODOpSyDkaR-bow/edit#gid=1515118726


## Singularity 
- **OK SO THIS JUST GOT BIGGER**
- We need to introduce using containers as a more normal feature
- This will likely get folded in with the python stuff
- https://github.com/comorment/containers
	- Oleks’ 


## Example Slurm jobs

