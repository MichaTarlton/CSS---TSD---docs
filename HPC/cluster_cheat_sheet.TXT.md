# cluster_cheat_sheet.TXT
Uh I think I got this from the wiki?

```
# for questions, please contact Max Korbmacher (max.korbmacher@gmail.com)
#############################################
###### CHEAT SHEET FOR TSD USAGE ############
#############################################

#############################
##### CLUSTER FUNCTIONS #####

# access to cluster
## there are different nodes to hop onto, specified after "ssh -Y"
ssh -Y p33-submit # got the handy mc viewer (recommended for quick access)
ssh -Y p33-appn-norment01 # preferred when using RStudio (no mc)
kinit # alternative cmd

# navigation, view and copy files
mc # installed on p33-submit but not on p33-appn-norment01!

#### Modules ####
# modules = software which you might need to load first before using it

# check whether a module is available
 module avail <software_of_your_choice> # e.g. python3
 # or
 module spider <software_of_your_choice>

#### R ####
# Use of RStudio (recommended to be used on appn-norment01)
ssh -Y p33-appn-norment01
module load R/4.1.0-foss-2021a
rstudio
# If you want to use xgboost in R: it is installed, and can  be called this way from p33-appn-norment01 

# run an R script
Rscript <script.R>

#### Python ####

# use of python (from your own virtual environment)
# check https://docs.python.org/3/library/venv.html
module load  Python/3.7.4-GCCcore-8.3.0
source /cluster/projects/p33/users/username/path/to/the/env # you need to define this path yourself, e.g. /cluster/projects/p33/users/maxk/py3/bin/activate 

# run python scripts
python3 <script.py>

#######################
##### DATA ACCESS #####

# for UKB: happens from /tsd/p33/data/durable/s3-api/ukbdata or /tsd/p33/data/durable/s3-api/ukblake

###########################
##### HELPFUL COMMANDS#####

# most importantly, use tab to complete and arrow up

# Open files with programs
soffice --calc <filename> # opens libre office calc
cat <filename> # reads file
gedit <filename> # opens file

# create new file and get access
chmod u=rwx << filename >>

# rename (and move)
mv orignial_name new_name 

# remove
rm <filename>

# permissions (give all allowances)
chmod 777 <filename>

# create new file
touch <filename>

# delete prefix in a set of files
for file in prefix*; do mv "$file" "${file#prefix}";done;

### QUEUEING ###
# add to queue
sbatch <filename> --acccount=p33_norment
sbatch <filename> --acccount=p33

#or for developer queue (debugging, don't run regular jobs)
sbatch --account=p33_norment_dev <file>

# check queue
squeue

# or your personal queue
squeue --user p33-user #user to be replaced w/ e.g. maxk

# To get an overview of all jobs (and whether it is ok to run more) check
qsumm

# check core usage
cost

# check core usage by person
cost --details

# check a specific job
squeue -j <JobId> 
# or
scontrol show job <JobId> # job id can be seen e.g. when using sbatch, in the slurm file or with squeue

# cancel job
scancel <filename>
```