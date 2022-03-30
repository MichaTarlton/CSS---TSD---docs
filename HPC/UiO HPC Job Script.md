# UiO HPC SLURM Job Script 
#norment #SLURM
**Clipped out of the [official help page](https://www.uio.no/english/services/it/research/sensitive-data/help/hpc/job-scripts.html)**

This page documents how to write job scripts to submit jobs on the Colossus (HPC for TSD) cluster.

To run a *job* on the cluster involves creating a shell script called a *job script*. The job script is a plain-text file containing any number of commslurmands, including your main computational task, i.e., it may copy or rename files, cd into the proper directory, etc., all before doing the "real" job. The lines in the script file are the commands to be executed, in the given order. Lines starting with a "#" are ignored as comments, except lines that start with a "`#SBATCH`" which are not executed, but contain special instructions to the [queue system](https://www.uio.no/english/services/it/research/sensitive-data/help/hpc/queue-system.html).

If you are not familiar with shell scripts, they are simply a set of commands that you could have typed at the command line. You can find more information about shell scripts here: [Introduction to Bash shell scripts](http://www.linuxconfig.org/Bash_scripting_Tutorial).

A job script consists of a couple of parts:

-   Instructions to the queue system
-   Commands to set up the execution environment
-   The actual commands you want to be run

Instruction parameters to the queue system may be specified on the sbatch command line and/or in `#SBATCH` lines in the job script. There can be as many `#SBATCH` lines as you need, and you can combine several parameters on the same line. If a parameter is specified both on the command line and in the jobscript, the parameter specified on the command line takes precedence. The `#SBATCH` lines should precede any commands in the script. A couple of parameters are compulsory. If they are not present, the job will not run:

-   **\--account**: Specifies the *project* the job will run in. If your project has a Sigma quota, this will be *project* (e.g. *p11*). If your project does not have a Sigma quota you'll need to use the tsd reservation, *project\_tsd* (e.g. *p11\_tsd*).
-   **\--time**: Specifies the maximal *wall clock time* of the job. Do not specify the limit too low, because the job will be killed if it has not finished within this time. On the other hand, shorter jobs will be started sooner, so do not specify longer than you need. The default maximum allowed **\--time** specification is 1 week; [see details here](https://www.uio.no/english/services/it/research/sensitive-data/help/hpc/queue-system.html#toc5).
-   **\--mem-per-cpu**: Specifies how much RAM each task (default is 1 task; see [Parallell Jobs](https://www.uio.no/english/services/it/research/sensitive-data/help/hpc/job-scripts.html#Parallel_Jobs)) of the job needs. Technically, this limit specifies the amount of resident memory + swap the job can use. If the job tries to use more than this setting, it will be killed. The maximum that can be requested it the available memory on the node (~500GB on the compute nodes). For instance:
    
    `#SBATCH --mem-per-cpu=2000M`
    
    If the job tries to use more than 2000 MiB resident memory requested in this example, it will be killed. Note that *\--mem-per-cpu* is specified per requested core.
    

The commands to set up the environment should include

module load *SomeProgram/SomeVersion*

jobsetup will set up needed environment variables and shell functions, and must be the first command in the script. module will set up environment variables to get access to the specified program.  It is recommended to specify the explicit version in the module load command.  We also encourage you to use

`module purge`

prior to the module load statements, to avoid inheriting unknown environment variable settings from the shell you use to submit the job.  We also advice using

`set -o errexit`

early in the script.  This makes the script exit immediately if any command below it fails, instead of simply going on to the next command.  This makes it much easier to find out whether anything went wrong in the job, and if so, where it happened.

 

## A Simple Serial Job

This is a script for running a simple, serial job

```
#!/bin/bash

# Job name:
#SBATCH --job-name=_YourJobname_
#
# Project:
#SBATCH --account=_YourProject_
#
# Wall clock limit:
#SBATCH --time=_hh:mm:ss_
#
# Max memory usage:
#SBATCH --mem-per-cpu=_Size_

## Set up job environment:
module purge   # clear any inherited modules
set -o errexit # exit on errors

## Copy input files to the work directory:
cp _MyInputFile_ $SCRATCH

## Make sure the results are copied back to the submit directory (see _Work Directory_ below):
chkfile _MyResultFile_ 
## Do some work:
cd $SCRATCH
_YourCommands_
```

Substitute real values for _YourJobname_, _YourProject_, _hh:mm:ss_, _Size_ (with 'M' for megabytes or 'G' for gigabytes; e.g. _200M_ or _1G_), _MyInputFile_, _MyResultFile_ and _YourCommands_.
