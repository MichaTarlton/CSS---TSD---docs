S3CMDFor importing and exporting large datasets.
Can be accessed via NREC machine.

[https://github.com/unioslo/tsd-s3cmd](https://github.com/unioslo/tsd-s3cmd) - date import & export API  (need to be on Uio network)



## tsd-s3cmd and TACL
> from NORMENT wiki: 
> https://wiki.norment.uiocloud.no/dokuwiki/tsd_import_export


These are two APIs for syncing the data to and from TSD via command line. These APIs can be only configured on certain systems (e.g. NIRD, SAGA, NREC, UCSD MMIL) because TSD has to while-list IP addresses. It's not possible to configure these APIs on a local laptop machine. Even on NIRD/SAGA/NREC/UCSD each user needs to install and configure tsd-s3cmd and TACL as described below.

tsd-s3cmd is more suitable for large scale incremental sync jobs with large number of files and complex folder structures. TACL is more suitable for interactive usage (more similar to the use of data portal, but from command line). Both API depend on python3 setup. If you don't have it configured, try as follows:

mkdir ~/miniconda3 && cd ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh 
bash Miniconda3-latest-Linux-x86_64.sh 
export PATH=$PATH:~/miniconda3/bin
The APIs won't work on a local laptop because the IP address needs to be white-listed. We have this configred for NIRD, MMIL and probably SAGA (not sure).

Usage of tsd-s3cmd is described here:

Note:

Once tsd-s3cmd is installed as mentioned in https://github.com/unioslo/tsd-s3cmd, create .config folder in the $HOME directory for registering the API.

 
cd && mkdir .config 
Useful commands:

tsd-s3cmd --guide
Note that the data will go into /tsd/p33/data/durable/s3api/<bucket>/.

TACL describe here: https://github.com/unioslo/tsd-api-client

The data will go to /tsd/p33/data/durable/file-import/p33-member-group/

It might be tricky to remove content of your TSD s3 bucket. If you have a bucket named MyBucket, and it has a folder MyFolder, you may remove the content of MyFolder in 2 steps: first, on your local machine, create an empty folder call MyFolder. Then, execute

tsd-s3cmd sync --no-check-md5 --delete-removed --force MyFolder s3://MyBucket