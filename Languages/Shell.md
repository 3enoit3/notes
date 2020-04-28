# Quotes and spaces
* '/" are not evaluated in "/' ("'$VAR'" is 'VAL')
* \ is only evaluated in " ("\\" is invalid, "\\"" is ", '\\' is \\, '\\'' is invalid but "\\'" is \\')
* concatenations are evaluated as a single argument ("1"'2'"3""4"5'6' is 123456) 
* variables:
  * $VAR means:
    * take the value of VAR
    * **field splitting**: build a list of strings by splitting the value on spaces
    * **filename generation**: expand wildcard for each strings
  * "$VAR" prevents from splitting/generating (but "$@" means "a1" "a2" "a3" ...)
```shell
> ls
f1.txt f2.out
> VAR='*.txt *.out'
> echo $VAR
f1.txt f2.out
> echo "$VAR"
*.txt *.out
```
  * to run $CMD, use eval
```shell
> cat f1.txt
hello world
> cat eval.sh
CMD='cat f1.txt | sed s/hello /hi /'
$CMD # cat complains |, sed, s/hello, /hi and / are not found
"$CMD" # shell complains cat f1.txt | sed s/hello /hi / is not found
eval $CMD # or eval "$CMD": eval interprets characters ($, |..) as they come, but sed complains s/hello is not valid

CMD2='cat f1.txt | sed '"'"'s/hello /hi /'"'"
eval $CMD2 # ok: hi world
```

# Tips
```shell
# Grep a stream (https://stackoverflow.com/a/7162898)
tail -f file | grep --line-buffered my_pattern

# Get script path (https://stackoverflow.com/a/4774063)
SCRIPTPATH="$( cd "$(dirname "$0")" >/dev/null 2>&1 ; pwd -P )"
```
