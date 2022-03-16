# Linux Quick Reference

# Functions
## cat

## comm
compares two sorted files and produces three columns of output, separated by tabs
https://www.oreilly.com/library/view/linux-pocket-guide/9780596806347/re67.html

**E.g.:**
`comm -23 metalist_woutfolders2.txt cleanedfilelist.txt > uncleanedlist.txt`

## cut and paste
https://linuxize.com/post/linux-cut-command/



How the cut function works:
clips part of a file, 
the `-f` grabs the “fields” default delimited by space.
Presumably the `5-` is to select fields 5 through end

I’m trying to figure out what the `<(...)` bullshit is, but I’m guessing part of the paste fnc
Nope, those must be some sort of “ feed into” thing like > is “output to” 

## echo

##  export
`export VARIABLENAME=` makes the variable available everywhere


## find
https://www.delftstack.com/howto/linux/linux-find-exec/

A `find` command is a useful tool for searching and selecting files in bash. We use the `find` command with some expressions and actions.

Example:

```bash
find ./folder -name *.txt
```

We use the `find` command with a search location, such as `./folder` for the `folder` directory and its sub-directories. And the `-name *.txt` expression is to find every `.txt` file in the location.

#### E.g. 
`find ${RAW} -type f | grep -E ${listname}.*cleansumstats_meta`


## grep
Search for particular pattern in a given file.
Basically do a text search on something 
https://www.delftstack.com/howto/linux/grep-command-in-linux/


## less 

## ls
**list directory contents**

![[ls colors]]

## mkdir
Create new directory

## mv
**Moving files**
[Lets's assume the dir structure is like,](https://stackoverflow.com/questions/4612157/how-to-use-mv-command-to-move-files-except-those-in-a-specific-directory)

```
|parent
    |--child1
    |--child2
    |--grandChild1
    |--grandChild2
    |--grandChild3
    |--grandChild4
    |--grandChild5
    |--grandChild6
```

And we need to move files so that it would appear like,

```
|parent
    |--child1
    |   |--grandChild1
    |   |--grandChild2
    |   |--grandChild3
    |   |--grandChild4
    |   |--grandChild5
    |   |--grandChild6
    |--child2
```

In this case, you need to exclude two directories `child1` and `child2`, and move rest of the directories in to `child1` directory.

use,
## this modification is for slurm only
##module load singularity/3.7.1  ## use this instead when running piecemeal
```
mv !(child1|child2) child1
```

This will move all of rest of the directories into `child1` directory.

Tip: Note however that using this pattern relies on `extglob`. You can enable it using `shopt -s extglob` (If you want `extended globs` to be turned on by default you can add `shopt -s extglob` to .bashrc) 



## rsync
> one way sync files to a location of your choice

rsync guide - [[How To Use Rsync to Sync Local and Remote Directories - 09.03.22]]
[Online](https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories)
https://linuxize.com/post/how-to-exclude-files-and-directories-with-rsync/
https://linuxize.com/post/how-to-use-rsync-for-local-and-remote-data-transfer-and-synchronization/
https://linux.die.net/man/1/rsync

`rsync -avP <source> <destination>`

`rsync -avzP  <source> <destination>  `  # with compression - for slow networks remote transfers

`-a` is Archive
> tells rsync to syncs directories recursively, transfer special and block devices, preserve symbolic links, modification times, groups, ownership, and permissions.

`-v, --verbose      `         
> increase verbosity
> This option increases the amount of information the daemon logs during its startup phase. After the client connects, the daemon's verbosity level will be controlled by the options that the client used and the lqmax verbosityrq setting in the module's config section.

`-P`, equivalent to `--partial` `--progress`. 
> When this option is used, rsync shows a progress bar during the transfer and keeps the partially transferred files. It is useful when transferring large files over slow or unstable network connections.

**E.g.:**

``` bash
rsync -avP cluster/projects/p697/projects/cleansumstats /cluster/projects/p697/users/michaejt
```

``` bash
rsync -avP --exclude={'out_dbsnp','out_1kgp','tmp'} /cluster/projects/p697/users/michaejt/cleansumstats /tsd/p697/home/p697-michaejt
```

## screen
see [[How to Use Linux Screen]]



## sed

E.g. `sed "${NUM}q;d" ${LIST}`

## wc
**Word Count**
Typically used by having the output of some file piped to it.

`wc -l` counts lines.

## zcat
Read a compressed file
See also: **cat**


# Guide to Combining Functions

# Guide to variables
https://tldp.org/LDP/abs/html/varassignment.html
https://www.metagenomics.wiki/tools/ubuntu-linux/shell-loop

## Bash Brackets
![[Bash Brackets Quick Reference - 17.02.22]]

## SSH
Connect to a linux machine 
`ssh <username>@<address>`
E.g. connnecting to NREC: `ssh michealt@158.39.200.231`
User will be subsequently prompted for a password, even if they do not have a user account.

### Saving SSH keys for easy connections
On the remote machine, if you have admin privileges, you can add the public key of the computer you are using to connect to the remote server. This allows the server to “recognize” your PC and not require a password.

Find and open the auth keys file in the .ssh directory in the root directory:
```
michealt@comorment:~/.ssh$ nano authorized_keys
```
And then add your public key to an open line and save.

#### Creating a key on local machine
`ssh-keygen` to create a new key
You can do so without a password.
This will create two files [where?], a private and public key.
The public key is the one you will save on the remote machine. The private one you should not need to share, like anywhere, ever.
Access the public key you created by looking in the `.ssh` folder on your local machine. It will have the name you gave it.

List all public keys with: `ls ~/.ssh/*.pub`
Show the key with `cat ~/.ssh/<name of your key>.pub`

https://stackoverflow.com/questions/3828164/how-do-i-access-my-ssh-public-key
[[Set up SSH public key authentication to connect to a remote system - 17.02.22]]

#### Saving remote server configuration on local machine
See [[Using the SSH Config File - 17.02.22]] [Online](https://linuxize.com/post/using-the-ssh-config-file/)

Saving a server host configuration allows for you to easily ssh to a remote server using an nickname. 
So instead of  `ssh michealt@158.39.200.231` I can connect using `ssh nrec`.

To do this first create a config file in your `.ssh` folder:
	`touch ~/.ssh/config` - create
	`chmod 600 ~/.ssh/config` - give user permissions and no one else
	`nano ~/.ssh/config` - open and edit

And save a configuration using the following template:
```
Host nrec
        HostName 158.39.200.231
        User michealt
```
Where `nrec` is the name I would like to use for connecting,
`HostName` is the ip-address of the remote server,
and `User` is my username.

