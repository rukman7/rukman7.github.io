---
layout: post
title: Bash scripting - basics
tags:
  - linux
  - bash
---
### Bash version tested
```
BruceWayne:[~] $ bash --version
GNU bash, version 3.2.57(1)-release (x86_64-apple-darwin18)
Copyright (C) 2007 Free Software Foundation, Inc
```

### Conditional statements
##### `if` condition
```bash
if EXPRESSION
  then DO SOMETHING
elif EXPRESSION
  then DO WHATEVER NEEDS TO BE DONE
else DO THE OTHERTHING
fi

#one liner
if CONDITION; then DO SOMETHING; elif EXPRESSION; then DO WHATEVER NEEDS TO BE DONE; else DO THE OTHERTHING; fi;
```
use `[[ ]]` when using variables in conditional statements. The whitespaces between `[[]]` is necessary.
```bash
#echoes if the file exists
if [[ -e $filename ]]
  then echo "file exists"
fi

#use ! for negation
#echoes if the directory does not exist
if ! [[ -e $dirname ]]
  then echo "directory does not exist"
fi
```
##### `for` loop
```bash
for ITEM in ITEMS;
  do echo $ITEM;
done
```
```bash
#example
BruceWayne:[~] $ for x in marvel dc; do echo $x; done
marvel
dc
BruceWayne:[~] $ 
```
Traditional C type for loop
```bash
for ((initialize; condition; expression))
do
  SOMETHING
done
#also supports break and continue.
```
##### 'while` loop
```bash
#syntax structue - while; do; done;
i="0"

while [ $i -lt 4 ]
do
  echo $i
  i=$[$i+1]
done
```
##### 'until' loop
```bash
#similar to while loop
#syntax structure - until; do; done;
```
### Command line arguments
* Use `$1` to get the first argument ,$2 for 2nd argument and so on..
* Use `*$` to get all arguments.
* Use `$#` to get count of arguments.
* `$@` prints all arguments.
  When called with double quotes ex: "$@", All arguments will be printed with each having double quotes.
  ```bash
  #example
  "arg1" "arg2" "arg3"
  ```
* `$*` similar to `$@` but when double quoted (ex: "$*"), All the arguments will be enclosed with in a single double quote.
  ```bash
  #example
  "arg1 arg2 arg3"
  ```
* If the no of arugements go beyond 9 curly braces should be used.
  ```bash
  #example
  echo $9
  echo ${10}
  ```
* `$0` - is special variable which prints the name of the file.

### Using regular expressions
```bash
if [[ "Han Solo" =~ ^Han ]]; then echo "star wars"; fi
```
The above code outputs:
```bash
BruceWayne:[~] $ if [[ "Han Solo" =~ ^Han ]]; then echo "star wars"; fi
star wars
BruceWayne:[~] $ 
# =~ succeeds if the string on the left has a match for regex on the right.
```

### Variables
* It's a good habbit to use curly braces around variables. For instance, While `$var` works but its better to have `${var}`.
* Attributes can be set to variables using `declare`. \ 
    ```bash
    #example
      declare -i test_var

      #Now $test_var will hold only numeric values. If a string is assigned to it, A zero will be set instead.
    ```
* We can use `declare +i test_var` to remove the attribute
* Also use `-r` (ex: `declare -ir test_var`) to make test_var read only
* Once test_var has been set with integer attribute, arithmetic operations can be performed.
  ```bash
  #example
  test_var="1+3"
  echo $test_var #will display 4
  ```

### Exporting variables
* By default variable's scope is within the script that is being executed.
* We cannot pass variables to another script. Even when a script is being execute inside its parent.
  To resolve this issue we can export variables
  ```bash
  #syntax
  export somevar=<value>
  declare -x somevar=<value>
  ```
##### Note:
1. Although exported variables can be accessed by all scripts in that environment, attributes cannot be exported along with variables.
	for instance: `declare -i x`. now `x` is an integer variable. but exporting it will make it loose integer property.
2. Subscript cannot pass variables to parent script even through exporting.

### Return codes
* A bash program always ends with a return code.
* If we use other programs in a bash script, It's good to know about the return codes of those programs.
* 0 - success & 1 to 255 - error.
* use `exit 1` to end program execution.

### Operators on strings

Operator | Meaning
------- | -------
-eq	| equality
-ne | not equal
-lt | less than
-gt | greater than
-z | returns true if a variable is empty

### Logical AND & OR
* AND `&&` - It executes 2nd statement only when the first statement succeeds.
  ```bash
  #example
  mkdir newdir && cd newdir
  ```
* OR `||` - It executes the 2nd statement only when the previous one fails.
  ```bash
  #example
  tk || echo "command not recognized"
  ```

### Switch case
```bash
#sample
case x in 
	pattern1)
		do something;;
	pattern2)
		do something;;
	pattern3)
		do something;;
	*)
		do somethiing;;
esac
```

### Command grouping
```bash
#syntax
{ command1; command2; command3; }
```
Use cases:
* Can use i/o redirection for the whole group.

### Arithmetic expressions
```bash
#syntax
(( expression here ))

#example
(( ++var )) #increments integer value in var by 1

#arithmetic variable assignment
#example
(( line_count = (cat file.txt | wc -l) ))
#line_count will hold integer which is the count of lines in file.txt

#command substitution for arithmetic expressions:
line_count=$((cat file.txt | wc -l))

let variable #holds integer
let x=10*10 #will hold 100
```

* `(( arithmetic expression ))` can also be used in `if`, While unlike other operations 0 is false and values greater than 0 is true.
```bash
#example
(( 0 )) || echo 'false' #this will output false
```
* Numbers leading with 0 will be interpreted as octal.
```bash
#example
#010 will be interpreted as 8
```

### Arrays
* Saving values in a array(no declaration required)
```bash
arr[0]="Chandler"
arr[1]="Joey"
arr[2]="Ross"
```
* Declaration
```bash
declare -a x
```
* Initializing
```bash
arr=(5,4,3,2,1,a,b,c)
```
* Retrieving a data from an array.
```bash
  echo ${arr[2]} #would out put "ross"

  #Retrieving all values
  echo ${x[@]}
  echo ${x[*]}

  #Get number of elements in the array
  echo ${#arr[@]}

  #Display indices instead of value
  echo ${!arr[@]}

  #Display indices and values
  echo declare -p arr
```

##### Note
1. Arrays cannot be exported.
2. We can also skip indices and directly put a value at any index.
```bash
#example
x[0]="Joey"
x[10]="Dr. Drake ramoray"
```