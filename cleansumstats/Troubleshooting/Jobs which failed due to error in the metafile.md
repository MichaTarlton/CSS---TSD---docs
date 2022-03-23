# Jobs which failed due to error in the metafile
Considered a precursor to [[7.1 Troubleshooting uncleaned sumstats]]
Not to considered current.


```
Jobs which failed due to error in the metafile

Column 'or' (from metadata field 'col_OR') did not exist in sumstat file header: [1, 729679, rs4951859, C, G, 1.03, 0.96, 1.10, .0288, .036, .4251, .19, .652, 15954, --+-+-++++++-+]
85 PGC_ASD_2017_CEU
86 PGC_ASD_2017_WW

---
---
$.col_CHR: null found, string expected
80 :
81
82
83
84

---
---
$.stats_TotalN: number found, integer expected
59 : fixed ALL
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
77
78

---
---
$.col_EffectAllele: is missing but it is required
34 BWGN_T1D_2009
46 ICBP_DBP_2011
47 ICBP_SBP_2011

---
---
Failed to match path regex error:  does not match the regex pattern ^[a-zA-Z0-9][a-zA-Z0-9_.-]+\.gz$
43 GIANT_BMI_2018_UKB_v2 '+'
44 GIANT_HEIGHT_2010 missing *.gz
45 GIANT_HEIGHT_2018_UKB fixed '+'


---
---
Failed to read/validate metadata file /cleansumstats/input/GAMEON_COLON_2015_CORECT.cleansumstats_meta: Column 'OR' (from metadata field 'col_OR') did not exist in sumstat file header: [markername,Rs_numbers,coordinate,Build,strand,nstudy,ncase,ncontrol,effect_allele,ref_allele,eaf,imp_type_mecc,imp_type_cfr1,imp_type_cfr2,imp_mecc,imp_cfr,beta,se,OR,L_CI,U_CI,pvalue]
37 COGS_PROSTATE_2013 
40 GAMEON_BREAST_2013_BCAC
41 GAMEON_COLON_2015_CORECT
```