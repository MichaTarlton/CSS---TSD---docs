# cleansumstats pipeline and SUMSTAT inventorycleansumstats pipeline and SUMSTAT inventory

@Mike, all of this is FYI, for now we'll keep working with Robert from UCSD on this,  but I'll keep you in the loop and in the long run you might take it over on our end in Oslo)  

@Rob, let's follow up about what we discussed for the cleansumstat pipeline ( [https://github.com/BioPsyk/cleansumstats/](https://github.com/BioPsyk/cleansumstats/) ) , and future organization of the SUMSTAT inventory on both ends ( MMIL / OSLO )

- I deployed cleansumstats pipeline on TSD in Oslo, following [https://github.com/BioPsyk/cleansumstats/blob/master/README.md](https://github.com/BioPsyk/cleansumstats/blob/master/README.md) (it was quite straighforward, I just had to build the references which took a few hours). And I'm quite happy with the way this pipeline  works, and with its results. It is really quite a lot  better than my previous ad-hoc solution based on the set of python_convert/sumstats.py scripts. I opened few issues  here - but none are show-stoppers:

[https://github.com/BioPsyk/cleansumstats/issues/259](https://github.com/BioPsyk/cleansumstats/issues/259)  

[https://github.com/BioPsyk/cleansumstats/issues/258](https://github.com/BioPsyk/cleansumstats/issues/258)  

[https://github.com/BioPsyk/cleansumstats/issues/257](https://github.com/BioPsyk/cleansumstats/issues/257)  

[https://github.com/BioPsyk/cleansumstats/issues/256](https://github.com/BioPsyk/cleansumstats/issues/256)  

[https://github.com/BioPsyk/cleansumstats/issues/251](https://github.com/BioPsyk/cleansumstats/issues/251)  

  

- I've auto-generated meta-data from my previous scripts, and stored this meta-data  on github.

[https://github.com/precimed/GWAS_SUMSTAT/tree/master/cleansumstats_meta](https://github.com/precimed/GWAS_SUMSTAT/tree/master/cleansumstats_meta)  

**Let's maintain this repo together - feel free to change meta-data to improve it, or add new files that are only relevant on your end!**   

From now on let's treat the meta-data as "master" - i.e. my old scripts and files such as [https://github.com/precimed/GWAS_SUMSTAT/blob/master/OF/all_sumstats.tsv](https://github.com/precimed/GWAS_SUMSTAT/blob/master/OF/all_sumstats.tsv) are no longer relevant.  

  

- The file tree under GWAS_SUMSTAT's "cleansumstats_meta" folder should be compatible with what you have under 
"/space/syn03/1/data/GWAS/SUMSTAT/RAW"  

- except that some files might be missing on your end (either because they are only available to Oslo's team due to data access restrictions, or because we downloaded files quire recently and haven't synced to your folders). I think we should assume that there are always files missing both on my end, and on your end - and we sync them if needed / if allowed.

Current limitation of cleansumstats.sh is that meta-file should be in the same folder as the data file - hence it's all organized in a file tree and not in a single folder. But perhaps it's an advantage - this way the structure of the cleansumstats_meta files reflect the structure of the actual data files. Also, the names of the .cleansumstats_meta files must match the output name, i.e. our <CONSORTIA>_<TRAIT>_<YEAR>_<COMMENT> scheme. I discuss this in 
[https://github.com/BioPsyk/cleansumstats/issues/251](https://github.com/BioPsyk/cleansumstats/issues/251) ticket - but perhaps it's fine, we can use it as it is.

  

- I trigger the pipeline using python script like this:

[https://github.com/precimed/GWAS_SUMSTAT/blob/master/make_slurm.py](https://github.com/precimed/GWAS_SUMSTAT/blob/master/make_slurm.py)  

which generates (and submits) a bunch SLURM scripts like this:

[https://github.com/precimed/GWAS_SUMSTAT/blob/master/SUMSTAT_DEMO.job](https://github.com/precimed/GWAS_SUMSTAT/blob/master/SUMSTAT_DEMO.job)  

and there are some further README notes here:

[https://github.com/precimed/GWAS_SUMSTAT/blob/master/README.md](https://github.com/precimed/GWAS_SUMSTAT/blob/master/README.md)  

  

I think we should independently run cleansumstats.sh pipeline both in Oslo and at UCSD using the same meta-data. And further processing stream of cleaned sumstats can be independent - no need to sync that for now.