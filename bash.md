# Bash

***

## String

### String Length

```bash
${#string}
```

### Substring in string

```bash
if [[ "$string" == *"$substring"* ]]; then
    echo "'$string' contains '$substring'";
else
    echo "'$string' does not contain '$substring'";
fi
```

### Substring Extraction

```bash
${string:position}
```

```bash
${string:position:length}
```

### Substring Removal

```bash
${string#substring}
```

> Deletes **shortest** match of \$substring from **front** of \$string.

```bash
${string##substring}
```

> Deletes **longest** match of \$substring from **front** of \$string.

```bash
${string%substring}
```

> Deletes **shortest** match of \$substring from **back** of \$string.

```bash
${string%%substring}
```

> Deletes **longest** match of \$substring from **back** of \$string.

### Substring Replacement

```bash
${string/substring/replacement}
```

> Replace **first** match of \$substring with \$replacement.

```bash
${string//substring/replacement}
```

> Replace **all** matches of \$substring with \$replacement.

```bash
${string/#substring/replacement}
```

> If \$substring matches **front end** of \$string, substitute \$replacement for \$substring.

```bash
${string/%substring/replacement}
```

> If \$substring matches **back end** of \$string, substitute \$replacement for \$substring.

## Redirection

### stderr --> file

```bash
grep da * 2> grep-errors.txt
```

### stderr --> stdout

```bash
grep * 2>&1
```

### stdout + stderr --> file

```bash
rm -f $(find / -name core) &> /dev/null
```


## Find in upper directory excluding **prune_me** sub-directory

```bash
find "upperdirectory" -not \( -path "upperdirectory/prune_me" -prune \) -exec bash -c 'echo "$0"' {} \;
```

## Bash perfs

```bash
SECONDS=0
some_code_here
t1=$SECONDS
suspected_very_slow_code_here
t2=$SECONDS
duration=$(( $t2 - $t1 ))
```

## Permissions

### simple

- directories: a+x
- files: a+r

```bash
chmod -R a+rX *
```

where **X** stand for :

```bash
$ man chmod
execute/search only if the file is a directory or already has execute permission for some user (X)
```

### with fine grained filter

- directories "755 (drwxr-xr-x)"
- files "644 (-rw-r--r--)"

```bash
chmod 755 $(find /path/to/base/dir -type d)
chmod 644 $(find /path/to/base/dir -type f)
```

## Path to the running script

### Note: If sourcing a script, $0 variable contains -bash

```bash
#!/bin/bash
BASEDIR="$(dirname $(readlink -f ${BASH_SOURCE[0]}))"
```

### How can I check bash syntax

+++ > [Shell Check](http://hackage.haskell.org/package/ShellCheck) < +++

### I have random errors running shell scripts

Check the system default shell!

```bash
$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 Jan 24  2017 /bin/sh -> dash
```

The default shell might be **dash** as in nowadays distros.
You may expect bash instead ...
To change to bash on debian and similar distro:

```bash
dpkg-reconfigure dash --> Use dash as default : No
```


## Misc



Re-execute last command



```bash

 !!

```



Execute number 3 command from history



```bash

 ! 3

```



Save last command to txt



```bash

 echo !! > txt

```



Kill to the end of the line and yank back



```bash

 find /etc/apache2/mods-available/ -mtime +1 | xargs ls -alh | awk '{print $9}'

 --> Cursor on 1st pipe then 

    Ctrl-k : find /etc/apache2/mods-available/ -mtime +1

    Ctrl-y : | xargs ls -alh | awk '{print $9}'

    Ctrl-u : suppresses words before cursor

```



tail alternative



```bash

 less +F /var/log/syslog

 Ctrl-c : detach and navigate in file

 Shift-F : re-attach

 q : exit

```



Jump into temporary shell editor



```bash

 $ for x in $LIST; do --> Ctrl-x-e

```



Paste arguments of last successful command



```bash

 Alt + .

```



What to do when terminal is misbehaving



```bash

 $ reset

```
