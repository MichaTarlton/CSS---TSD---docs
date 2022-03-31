# sumstat directory structure and files

## Primary working directories in the cluster
The primary working directory on the cluster is:
`/cluster/projects/p697/projects/`
This contains our cleansusmstats repo (the tool itself), the input sumstats, and the output folder for sumstats which are standardized. This directory has the structure:
```
/cluster/projects/p697/projects/
	|--cleansusmstats/
	|--SUMSTATv2_RAW/    
	|--SUMSTATv2_dev/
```
Where `cleansusmstats` is the repo directory,
`SUMSTATv2_RAW/` is the input file directory,
and `SUMSTATv2_dev` is the output directory.

You will copy the `cleansusmstats` folder to your personal directory, as shown in [[03 Creating a personal sandbox folder on cluster]].

The `SUMSTATv2_dev` folder you will leave alone for now as it is the directory with the “live” standardized sumstat files that are actively used for our research.

`SUMSTATv2_RAW/` contains the raw unstandardized sumstat files from outside studies. These files are organized into several (~100) subfolders. Each of these subfolders can contain one or more sets of sumstat files, though the actual directory structure can vary from folder to folder.

See [[SUMSTATv2_RAW Folder Structure]]



## sumstat folders and files
Each sumstat is a directory containing the summary statistics data as well as the associated metadata.
For example directory the directory  `SUMSTATSv2_RAW/GIANT_HEIGHT_2014`:
```
GIANT_HEIGHT_2014.cleansumstats_meta 
GIANT_HEIGHT_Wood_et al 2014.txt.gz
```
- Use `ls SUMSTATSv2_RAW/GIANT_HEIGHT_2014` to list a directory’s content like this 

`GIANT_HEIGHT_2014.cleansumstats_meta` is the metadata file. Any file ending with `*.cleansumstats_meta` is a metadata file. These are a YAML format file containing the column information for the associated genomic data file, and instruct CSS on how to interpret it. See an example metadata file in [[example cleansumstat_meta]]

`GIANT_HEIGHT_Wood_et al 2014.txt.gz` is the genomic data file taken from the outside study and contains the actual data. These are always compressed files ending with `.gz` These are input into CSS and standardized into a format usable by our researchers.


Each directory can contain more than one set of sumstat data. In fact we are more likely to see a directory which looks like:
```
GIANT BMI Speliotes2010 publicrelease HapMapCeuFreq.txt
GIANT BMI_Speliotes2010_publicrelease HapMapCeuFreq.txt.gz 
GIANT HEIGHT 2010.cleansumstats_meta
GIANT HEIGHT LangoAllen2016_publicrelease HapMapCeuFreq.txt 
GIANT HEIGHT LangoAllen2010_publicrelease HapMapCeuFreq.txt.gz 
GIANT WHRadjBMI_Heid2010_publicrelease HapMapCeuFreq.txt 
GIANT WHRadjBMI Heid2010_publicrelease HapMapCeuFreq.txt.gz Readme.txt
```

> Current limitation of cleansumstats.sh is that meta-file should be in the same folder as the data file - hence it's all organized in a file tree and not in a single folder. But perhaps it's an advantage - this way the structure of the cleansumstats_meta files reflect the structure of the actual data files. Also, the names of the .cleansumstats_meta files must match the output name, i.e. our `<CONSORTIA>_<TRAIT>_<YEAR>_<COMMENT>` scheme. I discuss this in  [https://github.com/BioPsyk/cleansumstats/issues/251](https://github.com/BioPsyk/cleansumstats/issues/251) ticket - but perhaps it's fine, we can use it as it is.
> 
> - Oleks


##  ADD SECTION ON THE DEV FOLDER AND TYPICAL CSS OUTPUT 

## Add about the metadata file YAML and info on that