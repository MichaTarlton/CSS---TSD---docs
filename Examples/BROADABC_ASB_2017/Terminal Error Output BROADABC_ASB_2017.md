# Terminal Error Output BROADABC_ASB_2017

``` shell
Execution cancelled -- Finishing pending tasks before exit
Error executing process > 'check_sumstat_format (1)'

Caused by:
  Process `check_sumstat_format (1)` terminated with an error exit status (1)

Command executed:

  # Sumstat file check on first 1000 lines
  echo "$(head -n 1000 < <(zcat BroadABC_METALoutput_Combined.tbl.gz))" | gzip -c > check_sumstat_format__sumstat_1000_rows
  check_and_format_sfile.sh check_sumstat_format__sumstat_1000_rows check_sumstat_format__sumstat_1000_rows_formatted check_sumstat_format__sumstat_1000_rows_formatted.log
  
  # Make second sumstat file check on all lines
  check_and_format_sfile.sh BroadABC_METALoutput_Combined.tbl.gz check_sumstat_format__sumstat_file check_sumstat_format__sumstat_file.log
  
  # Process before and after stats (the -1 is to remove the header count)
  rowsBefore="$(zcat BroadABC_METALoutput_Combined.tbl.gz | wc -l | awk '{print $1-1}')"
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
  /cleansumstats/work/3d/5d47d6f9de0144058ba1d6f6034261

Tip: you can replicate the issue by changing to the process work dir and entering the command `bash .command.run`

```