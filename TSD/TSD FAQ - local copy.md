# TSD FAQ - local copy
TSD (Tjenester for Sensitive Data) is a closed HPC facility where research projects store and analyze sensitive data.  
NORMENT's main TSD project is **p33** (TOP study). There are a few other NORMENT-partner TSD projects (**p697** for MoBa, **p830** for BupGen, **p970** for DemGene, **p1468** for BRAINMINT).  
TSD is available for all NORMENT personnel; access requires an 11-digits Norwegian national identification number (fødselsnummer), or a guest-account through international edu-institutions.

Read before you start [how\_to\_access\_tsd\_p33.pdf](https://wiki.norment.uiocloud.no/dokuwiki/_media/how_to_access_tsd_p33.pdf "how_to_access_tsd_p33.pdf (1.2 MB)")  
For Group leaders[how\_to\_provide\_access\_tsd\_p33.pdf](https://wiki.norment.uiocloud.no/dokuwiki/_media/how_to_provide_access_tsd_p33.pdf "how_to_provide_access_tsd_p33.pdf (774.1 KB)")

Note a new link to TSD documentation:

[https://www.uio.no/english/services/it/research/sensitive-data/help/](https://www.uio.no/english/services/it/research/sensitive-data/help/ "https://www.uio.no/english/services/it/research/sensitive-data/help/")

Note that if you already are registered on TSD, and are added to a new TSD project, you will need to reset your password (via [https://selfservice.tsd.usit.no/](https://selfservice.tsd.usit.no/ "https://selfservice.tsd.usit.no/") )

**Mail to all TSD p33 users:** tsd\-p33@medisin.uio.no  
**Mail to all TSD p33 HPC users:** norment-hpc@medisin.uio.no  
**Contact admin:** [oleksandr.frei@medisin.uio.no](mailto:oleksandr.frei@medisin.uio.no "oleksandr.frei@medisin.uio.no"), [thomas.bjella@medisin.uio.no](mailto:thomas.bjella@medisin.uio.no "thomas.bjella@medisin.uio.no"), [lavinia.athanasiu@ous-research.no](mailto:lavinia.athanasiu@ous-research.no "lavinia.athanasiu@ous-research.no"), Mads Lund Pedersen [m.l.pedersen@psykologi.uio.no](mailto:m.l.pedersen@psykologi.uio.no "m.l.pedersen@psykologi.uio.no"), [sandeep.karthikeyan@medisin.uio.no](mailto:sandeep.karthikeyan@medisin.uio.no "sandeep.karthikeyan@medisin.uio.no"), Sumair Hassan [Muhammad.Hassan@uib.no](mailto:Muhammad.Hassan@uib.no "Muhammad.Hassan@uib.no")

## Logging in to TSD

In your internet browser, open one of the following addresses:

You will need to provide your username, your one-time code and your password.  

You can choose between several virtual machines(e.g. win01, win02, win03). If one is busy, try the next.

## Norment web services

Within TSD, we have a few web services running, including NoDa (NORMENT database), Gitea (a Github-like service), and more.

To access them, open Firefox and type `p33-webserver.tsd.usit.no` into the address bar.

[![](https://wiki.norment.uiocloud.no/dokuwiki/_media/tsd_webservices.png?w=400&tok=779e4d)](https://wiki.norment.uiocloud.no/dokuwiki/_detail/tsd_webservices.png?id=tsd-faq "tsd_webservices.png")

### Norment Database

The “Norment Database” web service is where we can access our centers inhouse data. The web interface also allows you to improve the annotation of existing data or to upload your own data sets.

Please use “Norment Database test” to try things out first.

[![](https://wiki.norment.uiocloud.no/dokuwiki/_media/tsd_noda.png?w=300&tok=c0b5e2)](https://wiki.norment.uiocloud.no/dokuwiki/_detail/tsd_noda.png?id=tsd-faq "tsd_noda.png") [![](https://wiki.norment.uiocloud.no/dokuwiki/_media/tsd_noda_results.png?w=360&tok=2d4552)](https://wiki.norment.uiocloud.no/dokuwiki/_detail/tsd_noda_results.png?id=tsd-faq "tsd_noda_results.png")

## Connect to our network disk

This is a [step-by-step guide](https://www.uio.no/english/services/it/research/sensitive-data/use-tsd/directories-files/shortcuts/index.html "https://www.uio.no/english/services/it/research/sensitive-data/use-tsd/directories-files/shortcuts/index.html") to access folders in **TSD\-Windows:**  

Use this address:

1.  `\\tsd-evs\p33`  
    (corresponds to the Linux directory `/tsd/p33/…`)
    

## Monitor your memory (RAM) usage

## Where to store data?

For personal stuff, we use `/tsd/p33/data/durable/characters/<username>` and, for data that needs to be accessible from TSD's computing cluster `/cluster/projects/p33/users/<username>`. What is meant here with <username> is the user's login name deprived of the `p33-` prefix. Should any of these spaces not be accessible please contact an administrator. See also the [TSD directory structure](https://wiki.norment.uiocloud.no/dokuwiki/tsd_directory_structure "tsd_directory_structure") for more info. Users are also assigned a home space in `/tsd/p33/home`, however, this space is only supposed to contain configuration files and such, and storage of large amounts of data there is strongly discouraged.

If you store temporary data, please put it under a directory branch labelled `no-backup` or use the existing directory `/tsd/p33/data/no-backup/`. This will exclude the data from the backup services and thereby lower the costs of storing data.

To check available disk space, look at the file `/tsd/p33/data/durable/projectinfo/disk_usage.txt`.

On Windows machine, please avoid storing data on C:\\ drive. This is really important, because C:\\ drive is small, and all Windows users of the TSD project will be affected if you run out of disk.

## Linux Machines

**App nodes**. App nodes are powerful physical servers you can connect with “ssh” and use interactively. They are similar in configuration to the p33-submit machines, except they are a lot more powerfull. Each app node have local installation singularity, eog, nano, gedit, rstudio. Each app node 54 TB of local storage space (mounted on /storage). Use this at your own risk, as this has no backup (though it is a RAID with 2 redundant disks). Each p33 and p697 project have it's own app node, not accessible from another TSD project:

p33-appn-norment01 (Red Hat 7) - 128 CPUs, 1536 GB memory, GPU (NVIDIA Tesla V100S)
p697-appn-norment01 (Red Hat 7) - 64 CPUs, 512 GB memory

**Linux machines (p33)**. By default new users are assigned to p33-tl01-l machine for remote access via ThinLink. User can request TSD to switch their ThinLink login machine to p33-rhel7-login. After connecting to login machine it is highly recommended to ssh to the app node or a p33-submit\[2,3\] host.

p33-rhel8-01      (Red Hat 8) - 4 CPUs, 64 GB memory
p33-rhel8-02      (Red Hat 8) - 4 CPUs, 8 GB memory
p33-submit        (Red Hat 7) - 8 CPUs, 64 GB memory
p33-submit2       (Red Hat 7) - 8 CPUs, 64 GB memory
p33-submit3       (Red Hat 7) - 8 CPUs, 128 GB memory  

**Linux machines (p697)**:

p697-rhel8-01     (Red Hat 8) - 4 CPUs 64 GB memory
p697-submit       (Red Hat 7) - 8 CPUs, 64 GB memory
p697-submit2      (Red Hat 7) - 8 CPUs, 256 GB memory

Once logged onto one of these, the others can be accessed via `ssh`.

## Disk quotas

/cluster/projects/p33             - 700 TB
/tsd/p33/data/durable             - 150 TB
/tsd/p33/data/colossus            - 1 TB
/tsd/p33/home                     - 11 TB
/tsd/p33shared/durable            - 1 TB
/tsd/p33sharedp229/data/durable   - 0.5 TB
/tsd/p33sharedp29/data/durable    - 1 TB
/tsd/p33sharedp471/data/durable   - 1 TB
/tsd/p33sharedp697/data/durable   - 10 TB
/cluster/projects/p697            - 40 TB
/tsd/p697/data/durable            - 20 TB
/tsd/p697/home                    - 1 TB
/tsd/p697sharedp33/data/durable   - 10 TB
/tsd/p697sharedp471/data/durable  - 1 TB
/tsd/p697sharedp315/data/durable  - 1 TB

## Tentative responsibilities of group delegates

\- admin export rights for the users from multimodal imaging group - communicate the needs and issues raised by the users in multimodal imaging group to DB CRU - when it comes to issues, double-check that they are internally discussed in multimodal imaging group, attempting to find someone in your group who already had an expertice with this - coordinate cleanup efforts / disk space usage (if we exceed the quota)
