# matchlines.sh
Taken from
https://unix.stackexchange.com/questions/172376/how-do-i-efficiently-select-specific-line-numbers-from-a-list-of-records
```shell
awk 'NR == FNR{a[$0]; next};FNR in a' linenumbers.txt sourcefile.csv > extractedrecords.tsv
```
Modified and put into my p697 github repo under precimed.
Note that this will output a sorted list (by line number)