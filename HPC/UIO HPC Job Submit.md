# UIO HPC Job Submit
https://www.uio.no/english/services/it/research/sensitive-data/help/hpc/queue-system.html
## Submitting a job

To run a job on the cluster, you submit a [job script](https://www.uio.no/english/services/it/research/sensitive-data/help/hpc/job-scripts.html) into the _job queue_, and the job is started when one or more suitable _compute nodes_ are available. The job queue is managed by a queue system (scheduler and resource manager) called Slurm [(Slurm's documentation page)](http://slurm.schedmd.com/).

Please note that jobscript names should not contain sensitive information.

[Job scripts](https://www.uio.no/english/services/it/research/sensitive-data/help/hpc/job-scripts.html) are submitted with the sbatch command:

`sbatch _YourJobscript_`

The sbatch command returns a _jobid_, an id number that identifies the submitted job. The job will be waiting in the job queue until there are free compute resources it can use. A job in that state is said to be _pending_ (_PD_). When it has started, it is called _running_ (_R_). Any output (stdout or stderr) of the job script will be written to a file called slurm-_jobid_.out in the directory where you ran sbatch, unless otherwise specified.

All commands in the job script are performed on the compute-node(s) allocated by the queue system. The script also specifies a number of requirements (memory usage, number of CPUs, run-time, etc.), used by the queue system to find one or more suitable machines for your job.

You can cancel running or pending (waiting) jobs with scancel:

```
scancel _jobid_ # Cancel job with id _jobid_ (as returned from sbatch)
scancel --user=_MyUsername_    # Cancel all your jobs
scancel --account=_MyProject_  # Cancel all jobs in _MyProject_
```
See man scancel for more details.