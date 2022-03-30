# BROADABC_ASB_2017 – check_sumstat_format_sumstat_file.log

This is the log file called `check_sumstat_format_sumstat_file.log` which can be found in the work directory we specified to css using the `-w` option, or will be put in a default directory that looks something like `/cleansumstats/work/3d/<”longhexnumber">`.

`bash-4.2$ cat check_sumstat_format_sumstat_file.log `

```
##############################
gziptest
##############################
gzip-check1 ok


##############################
force space separators as tab-sep
##############################
tab-sep-enforce1 ok


##############################
Check if the header is treated like only one field
##############################
header-check1 ok
header-check2 ok


##############################
tab-sep-NF-same
##############################
tab-sep1 fail ::: not all rows had same number of fields after tab enforcement
tab-sep2 ok


something failed during basic checks, not proceeding to testing the whole file
gziptest_result ok
tab_sep_result1 ok
one_field_header_result1 ok
one_field_header_result2 ok
tab_sep_NF_result1 fail ::: not all rows had same number of fields after tab enforcement
tab_sep_NF_result2 ok

```