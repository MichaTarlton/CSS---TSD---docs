# How to extract directory path from file path?
>  https://stackoverflow.com/questions/6121091/how-to-extract-directory-path-from-file-path
```shell
$ export VAR=/home/me/mydir/file.c
$ export DIR=${VAR%/*}
$ echo "${DIR}"
/home/me/mydir

$ echo "${VAR##*/}"
file.c
```
To avoid dependency with `basename` and `dirname`

---

`dirname` and `basename` are the tools you're looking for for extracting path components:
```shell
$ VAR='/home/pax/file.c'
$ DIR="$(dirname "${VAR}")" ; FILE="$(basename "${VAR}")"
$ echo "[${DIR}] [${FILE}]"
[/home/pax] [file.c]

```
They're not internal bash commands but they are part of the POSIX standard - see dirname and basename. Hence, they're probably available on, or can be obtained for, most platforms that are capable of running bash.


---

On a related note, if you only have the filename or relative path, dirname on its own won't help. For me, the answer ended up being readlink.
```shell
fname='txtfile'    
echo $(dirname "$fname")                # output: .
echo $(readlink -f "$fname")            # output: /home/me/work/txtfile
```
You can then combine the two to get just the directory.

```shell
echo $(dirname $(readlink -f "$fname")) # output: /home/me/work
```