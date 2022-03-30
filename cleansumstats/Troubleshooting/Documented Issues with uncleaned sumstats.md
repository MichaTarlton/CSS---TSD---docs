# Documented Issues with uncleaned sumstats
Taken from the text file in my login node scratch directory: `Documented issues with the 19 - 98.txt`

This is referring to [[20. Academia/01 NORMENT/CSS Documentation/cleansumstats/uncleanedlist.txt|uncleanedlist.txt]]  
Where the numbers refer to line 
the 19 - 98

---
## 22, 23, 97, 38, 36, 48, 32, 76, 90, 89, 20, 21, 27, 24, 26, 25, 31, 30, 29, 28
FIXED!

---
## 85, 86
 Reading metadata files
Postprocess metadata
Failed to read/validate metadata file /cleansumstats/input/PGC_ASD_2017_WW.cleansumstats_meta: Column 'or' (from metadata field 'col_OR') did not exist in sumstat file header: [1, 729679, rs4951859, C, G, 1.03, 0.96, 1.10, .0288, .036, .4251, .19, .652, 15954, --+-+-++++++-+]


---
## 80, 81, 82, 83, 84

Reading metadata files
Failed to read/validate metadata file /cleansumstats/input/NORMENT_BRAINSTEMVOLUMES_2019_Whole.cleansumstats_meta: - $.col_CHR: null found, string expected


---
## 35, 92, 96, 98

mkdir: cannot create directory ‘out’: Permission denied
outdir doesn't exist

---
## 52, 54, 33

Can't lock file: /cleansumstats/tmp/fake-home/.nextflow/history -- Nextflow needs to run in a file system that supports file locks

---
## 67, 66, 65, 64, 61, 59, 63, 62, 60, 69, 78, 77, 75, 74, 73, 72, 71, 70, 68

Reading metadata files
Failed to read/validate metadata file /cleansumstats/input/MAGIC_GLYCEMIC_2021_FG_SAS.cleansumstats_meta: - $.stats_TotalN: number found, integer expected


---
## 46, 34, 47

Reading metadata files
Failed to read/validate metadata file /cleansumstats/input/ICBP_DBP_2011.cleansumstats_meta: - $.col_EffectAllele: is missing but it is required

---
## 45, 44, 43,
Reading metadata files
Failed to read/validate metadata file /cleansumstats/input/GIANT_HEIGHT_2018_UKB.cleansumstats_meta: - $.path_sumStats: does not match the regex pattern ^[a-zA-Z0-9][a-zA-Z0-9_.-]+\.gz$

---
## 41, 40, 37 
Reading metadata files
Postprocess metadata
Failed to read/validate metadata file /cleansumstats/input/GAMEON_COLON_2015_CORECT.cleansumstats_meta: Column 'OR' (from metadata field 'col_OR') did not exist in sumstat file header: [markername,Rs_numbers,coordinate,Build,strand,nstudy,ncase,ncontrol,effect_allele,ref_allele,eaf,imp_type_mecc,imp_type_cfr1,imp_type_cfr2,imp_mecc,imp_cfr,beta,se,OR,L_CI,U_CI,pvalue]



---









---
---

# The error output of the next 15 files are similar but the defining feature of the errors is unclear to me.
# See the one immediately below for a good example.

---
## 93, 42, 39, 58, 57, 56, 55, 51, 50, 49, 53, 87, 79, 88, 91,

Caused by:
  Process `check_sumstat_format (1)` terminated with an error exit status (1)

Command executed:

  # Sumstat file check on first 1000 lines
  echo "$(head -n 1000 < <(zcat daner_pgc_mdd_meta_no23andMe_noUKBB.gz))" | gzip -c > check_sumstat_format__sumstat_1000_rows
  check_and_format_sfile.sh check_sumstat_format__sumstat_1000_rows check_sumstat_format__sumstat_1000_rows_formatted check_sumstat_format__sumstat_1000_rows_formatted.log
  
  # Make second sumstat file check on all lines
  check_and_format_sfile.sh daner_pgc_mdd_meta_no23andMe_noUKBB.gz check_sumstat_format__sumstat_file check_sumstat_format__sumstat_file.log
  
  # Process before and after stats (the -1 is to remove the header count)
  rowsBefore="$(zcat daner_pgc_mdd_meta_no23andMe_noUKBB.gz | wc -l | awk '{print $1-1}')"
  rowsAfter="$(wc -l check_sumstat_format__sumstat_file | awk '{print $1-1}')"
  echo -e "$rowsBefore	$rowsAfter	Force tab separation" > check_sumstat_format__desc_force_tab_sep_BA.txt

Command exit status:
  1

Command output:
  (empty)

Command error:
  
  gzip: stdout: Broken pipe
  /cleansumstats/bin/check_and_format_sfile.sh: line 86: [: too many arguments
  one or more problems detected with the meta data format, see logfile

Work dir:
  /cleansumstats/tmp/fake-home/work/ea/3c25a7301cb19fb28f7e10fbed70e2

Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`


---
