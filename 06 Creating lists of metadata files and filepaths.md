
# Creating lists of metadata files and filepaths

### Command for finding processed files
Because the processed and output file is `cleaned_GRCh37.sumstats.gz`, we can find which sumstat files have already been processed by searching for the folders that have this output in the `SUMSTATSv2_dev` folder.

We can do such with this script:
``` shell
cd /cluster/projects/p697/projects/SUMSTATv2_dev/cleansumstats 
find . -type f | grep cleaned_GRCh37.sumstats.gz
```

Which will create an output that looks something like:
```
./UKF_CeD_2016/cleaned_GRCh37.sumstats.gz # 06 Creating lists of metadata files and filepaths

./UNC_IL37_2018/cleaned_GRCh37.sunstats.gz
./UKB_SLEEP_2016/cleaned_GRCh37.sumstats.gz ./PGC_BIP_2016_typel/cleaned_GRCh37.sumstats.gz ./IIBDGC_IBD_2817/cleaned_GRCh37.sumstats.gz ./UKB_ANX_2019_EFFECT/cleaned_GRCh37.sumstats.gz ./UKB_LIFESPAN_2019/cleaned_GRCh37.sumstats.gz ./GIANT_BMI_2015_EUR/cleaned_GRCh37.sumstats.gz ./ANGST_ANX_2016_FS/cleaned_GRCh37.sumstats.gz
```
Albeit much longer. 

### Making a list of all  clean output files
Using the above as a starter, we can create a list of all sumstats (by metadata filename) which have already been successfully processed.
``` shell
cd /cluster/projects/p697/projects/SUMSTATv2_dev/cleansumstats 

find . -type f | grep cleaned_GRCh37.sumstats.gz | sort > /cluster/projects/p697/users/michaejt/lists/cleanedlist.txt`
```

The `sort` function will alphabetically sort the output we take from the initial output list, and `>` will save that output list as file `cleanedlist.txt`  in a folder I have made in my sandbox directory called `lists`.

### Making a list of folders in the SUMSTATv2_RAW folder
We can list all directories in the current folder using: `ls -d */` .
So using this we can save a list of all the folder names in the sumstat input files using:
``` shell
cd /cluster/projects/p697/projects/SUMSTATv2_RAW/ 

ls -d */ > /cluster/projects/p697/users/michaejt/lists/folderlist _SUMSTATSv2_RAW.txt 
``` 

However, because there can be more than one set of sumstat data per folder, we will want to retrieve a list of the metadata files  


### Making a list of all available metadata files
Simply put:
``` shell
cd /cluster/projects/p697/projects/SUMSTATv2_RAW/ 

find . -type f | grep '.cleansumstats_meta' | sort  > /cluster/projects/p697/users/michaejt/lists/metalist.txt
``` 

This will give us an output file that looks a little like:
```
...
UKF_CeD_2010/UKF_CeD_2010.cleansumstats_meta
UNC_IL37_2018/UNC_IL37_2018.cleansumstats_meta
UKB_SLEEP_2016/UKB_SLEEP_2016.cleansumstats_meta
UKB_LIFESPAN_2019/UKB_LIFESPAN_2019.cleansumstats_meta
GIANT_BMI_2015_EUR/GIANT_BMI_2015_EUR.cleansumstats_meta
...
```

We can see that this list includes the folder names where the metadata files are found. We may however want only the names of the metadata files.

### List of metadata without folders 
Using a text editor that supports find-replace using [RegEx](https://regexr.com) such as [Sublime Text](https://www.sublimetext.com) or [VS Code](https://code.visualstudio.com) (use of either is highly recommended and if you are working on a Windows VM login node it already has VS Code installed) you can select everything up until the `/` on each line using the regex search `.+?/` and then “replace-all” with nothing.

Likewise, to remove the file extension, you can replace-all `.cleansumstats_meta` with nothing as well. This will be useful in maintaining a list of only filenames.

I choose to save this as a separate file called `metalist_woutfolders.txt` as you may want to keep the list with folder names down the line. You may then want to alphabetically sort this list as the original was sorted by the folder names. You can do so by using the sort function again, or with the text editors’ built in sort functions.

### Identifying unprocessed sumstats
Because the processed files will be folder named by the metadata file that was used, we can compare our lists of “raw” metadata with the list of processed sumstats. 

Using a similar replace-all method on the `cleanedlist.txt` you can remove everything except the folder names (it is up to you if you would like to save this list as a separate file, but I find it unnecessary).

We compare our list of raw metadata names with our list of processed sumstats names using:
``` shell
comm -23 metalist_woutfolders.txt cleanedlist.txt > uncleanedlist.txt
```
Which gives us a list of all sumstat names in `metalist_woutfolders.txt` *but not* in `cleanedlist.txt`. We save this in `uncleanedlist.txt`.

We can then investigate why these sumstats are not processed or what caused them to fail.


###  **OUTCOME**
By this process, and as of February 2022, we have identified the following:
Number of folders in RAW input directory: **184** 
Number of metadata input files: **362**
Number of cleaned output files: **264**
Number of uncleaned files: **98**
Though this may have changed since this was written.
Try it out for yourself and bug Nadine if you find anything.

## Example Lists
You asked for them so here you go:

[[metadata list]]
[[metadata list without folders or file extensions]]
[[cleaned sumstats list]]
[[uncleaned sumstats list]]