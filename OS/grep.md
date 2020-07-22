###### Global Regular Expressions Print
```
# search a line which will start from only A-Z, a-z & 0-9
grep "^[[:alnum:]]" file.txt

# search line which will start from only [A-Z & a-z]
grep "^[[:alpha:]]" file.txt

# search line which will start from digit [0-9]
grep "^[[:digit:]]" file.txt

# search line which will start from [! ” # $ % & ‘ ( ) * + , – . / : ; < = > ? @ [ \ ] ^ _ ` { | } ~. ] 
grep "^[[:punct:]]" file.txt

# search a line which will start from [tab, newline, vertical tab, form feed, carriage return, and space]
grep "^[[:space:]]" file.txt

# search a line which will start from [A-Z]
grep "^[[:upper:]]" file.txt

# Search Hexadecimal Digits
grep "^[[:xdigit:]]" file.txt

ip address from list of files:
cat * | grep -E -o '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}'

replace a string in multiple files (say, every .html file)
find . -type f -name '*.html' -exec sed -i -e 's/SEARCHTEXT/REPLACETEXT/g' {} \;

# GENERAL
# print lines begining with range of letters
grep ^[A-D] table.txt

# REGEX
# search for word which has any single character followed by ello
grep ".ello" demo.txt

# OR, all the below examples produce the same results
grep "stuff\|more" demo.txt
grep -E "stuff|more" demo.txt
grep -e "stuff" -e "more" demo.txt

# AND, there is no AND so regex works
grep 'Manager.*Sales' employee.txt

# AND & OR
grep 'Manager.*Sales\|Developer*Tech' employee.txt

# begin with 1 and endswith C
grep '^1.*C$' file.txt

# FLAGS
# print everything that doesn't contain the query
grep -v ^Da* table.txt

# -i forgets about case sensitivity
grep -i ^DA table.txt

# show only the matched string, not the entire line in which it is present within.
grep -o "Meow" table.txt

# print the file containing the query including thos within subdirs
grep -r ^David ~/scripts-x14.04/bash/*

# print the name of the file(s) which matches the query
grep -l ^David ~/some_dir/*

# count the number of matches
grep -c "stuff" table.txt

# show the line numbers of the matches
grep -n "go" demo.txt

# search only for the full word
grep -w "of" table.txt

# print 3 lines after the match (-B for before the match & -C for before and after)
grep -A 3 "of" table.txt

#Some Examples
egrep 'mellon' myfile.txt #Print every line in myfile.txt containing the string 'mellon'.
egrep -n 'mellon' myfile.txt #Same as above but print a line number before each line.
egrep '(.)bb\1' myfile.txt #Find every line with 2 b's and the same character both before and after those b's.
egrep -l '[0-9]{8,}' /files/projectx/* #Print each file in the directory projectx which contains a number of 8 digits or more.
egrep '\b[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,4}\b' myfile.txt #Print every line of myfiles.txt containing an email address.
#Note: this is just a simple email matching pattern. There is a miniscule number of email addresses it will not match.
```
```
egrep
fgrep
pgrep
```
###### regex
```
Basic Usage
egrep or 
grep -E
Run grep with extended regular expressions.
-i Ignore case (ie uppercase, lowercase letters).
-v Return all lines which don't match the pattern.
-w Select only matches that form whole words.
-c Print a count of matching lines.
Can be combined with the -v option to print a count of non matchine lines.
-l Print the name of each file which contains a match.
Normally used when grep is invoked with wildcards for the file argument.
-n Print the line number before each line that matches.
-r Recursive, read all files in given directory and subdirectories.

Regular Expressions
.  A single character
[abc] Range. ie any one of these characters
[^abc] Not range. A character that is not one of those enclosed.
(abc) Group these characters and remember for later.
\n Replace n with a number. Recall the charactes matched in that set of brackets.
May also be used to rename files or directories.
| The logical 'or' operation.
\ In front of a character, removes it's special meaning.

RE Multipliers
?  The preceding item is optional, it is matched zero or one times.
* The preceding item will be matched zero or more times.
+ The preceding item will be matched one or more times.
{n} The preceding item will be matched exactly n times.
{n,} The preceding item will be matched n or more times.
{n,m} The preceding item will be matched between n and m times.

RE Anchors
^ From the beginning of the line.
$ To the end of the line.
\< At the beginning of a word.
\> At the end of a word.
\b Match either the beginning or end of a word.

```
