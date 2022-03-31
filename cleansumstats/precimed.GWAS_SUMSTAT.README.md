# precimed.GWAS_SUMSTAT README

This repository contains meta-data associated with MMIL-OSLO inventory of summary statistics:
https://docs.google.com/spreadsheets/d/19cURugXQQyLgfLU-gwCReuWK99DcpODOpSyDkaR-bow/edit#gid=1515118726

It depends on https://github.com/BioPsyk/cleansumstats tool to harmonize the data. 
As a result, all data is converted GRC37 as well as GRC38 builds,
with consistent naming of columns across all files,
and consistent choice of effect & other alleles.

Current limitations are that
- not all resulting files have sample size (but it's available in the meta-data files)
- some resulting files don't have Z score (https://github.com/BioPsyk/cleansumstats/issues/257)
- A/T and C/G markers are dropped (although this might be a good idea that saves a lot of potential errors)
- indels and other markers are dropped
- variants without an rs# in dbSNP are dropped

These are the steps required to run the pipeline:

1. clone this repository

2. ensure that this repository is in sync with meta-data stored together with the data, i.e. here:
   ```
	export RAW=/space/syn03/1/data/GWAS/SUMSTAT/RAW            # at MMIL
	export RAW=/cluster/projects/p697/projects/SUMSTATv2_RAW   # on TSD
   ```
   This is to make sure that you're not going to overwrite 
   someone's changes in the meta files. To do so, prior to implementing your 
   changes in cleansumstats_meta folder of this repo, do like this:

   - remove cleansumstats_meta folder of this repository
   - make a tar.gz file containing a copy out all meta-files within RAW folder using this command:
   ```
   cd $RAW && find . -name '*.cleansumstats_meta' -print0 | tar -czvf meta.tar.gz --null --files-from -
   ```
   - extract meta.tar.gz into /cleansumstats_meta subfolder of this repo
   - if there are changes, investigate which version is newer - and merge if there are conflicts.
     commit newer changes to this repository.

3. Now you can implement your changes to meta-files, and copy them over to the RAW folder.

4. Adjust and run ``python make_slurm.py`` script.

ToDo:

* The following traits require some attention as they don't have effect direction.
  They are marked with ``True`` in ``a1inc`` column of the ``all_sumstats.tsv``  file.
  They are so old that it might be relevant to just exclude them from the inventory.

  ```
  DIAGRAM_T2D_2016
  GIANT_HEIGHT_2010
  ICBP_SBP_2011
  ICBP_DBP_2011
  BWGN_T1D_2009
  FTLD_TDP43_2008
  ```

* 23andMe data format isn't supported by cleansumstats pipeline as it's split into two files


