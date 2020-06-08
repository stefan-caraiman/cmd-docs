# awk

print lines matching `foo`
    awk '/foo/' input.txt

match foo, split on whitespace, and print the first element in the split array
    awk '/foo/ { print $1 }' input.txt

use `:` as the field delimiter
    awk -F:


# Basic Usage

Print a subset of lines from a file:
    awk '/<pattern>/' <inputfile>

The forward slashes around `<pattern>` are required for POSIX-style regular
expressions.

Wrap everything going to `awk` in single quotes and give it the name of an
input file.

More complicated processing of matching lines can go in curly braces. For
example, this command will print each line that matches foo:
    awk '/foo/ { print }' input.txt


# Print Matching Lines

`awk` prints lines by default, so no command prints the whole matching line.
`$0` is special and means the whole matching line. The following three commands
are all equivalent. Each will print every line from a file matching `foo`
(`/foo/`) (output is not shown):
    $ awk '/foo/' input.txt
    $ awk '/foo/ { print }' input.txt
    $ awk '/foo/ { print $0 }' input.txt


# Columns and Fields

`awk` divides each lines into an array of "fields", much like `split`. By
default it splits on whitespace.

Fields are referred to by a `$` and an index. `$2` means the second field in
the line.

Fields are 1-indexed--i.e. `$2` would refer to the second column in a file.

`thrones.txt`:
    Tyrion   Lannister    555.360.1234
    Jamie    Lannister    555.360.9876
    Jon      Snow         555.206.4444
    Arya     Stark        555.206.1111

Match lines containing `Lannister`, print the first field (split on
whitespace):
    $ awk '/Lannister/ { print $1 }' thrones.txt
    Tyrion
    Jamie


# For Loops

For loops can be used to do things like print all the fields in a line. Here
`NF` is the number of fields on every line in the file `input.txt`. We match
all lines (by not giving a pattern) and print all fields, splitting on
whitespace by default:
    awk '{ for (i = 1; i < NF; i++) print $i }' input.txt

# awk                                                                                         
                                                                                              
  A versatile programming language for working on files.                                      
  More information: <https://github.com/onetrueawk/awk>.                                      
                                                                                              
- Print the fifth column (a.k.a. field) in a space-separated file:                            
                                                                                              
  awk '{print $5}' filename                                                                   
                                                                                              
- Print the second column of the lines containing "something" in a space-separated file:      
                                                                                              
  awk '/something/ {print $2}' filename                                                       
                                                                                              
- Print the last column of each line in a file, using a comma (instead of space) as a field separator:
                                                                                              
  awk -F ',' '{print $NF}' filename                                                           
                                                                                              
- Sum the values in the first column of a file and print the total:                           
                                                                                              
  awk '{s+=$1} END {print s}' filename                                                        
                                                                                              
- Sum the values in the first column and pretty-print the values and then the total:          
                                                                                              
  awk '{s+=$1; print $1} END {print "--------"; print s}' filename                            
                                                                                              
- Print every third line starting from the first line:                                        
                                                                                              
  awk 'NR%3==1' filename                                                                      
                                                                                              
- Print all values starting from the third column:                                            
                                                                                              
  awk '{for (i=3; i <= NF; i++) printf $i""FS; print""}' filename                             
                                                                                              
- Print different values based on conditions:                                                 
                                                                                              
  awk '{if ($1 == "foo") print "Exact match foo"; else if ($1 ~ "bar") print "Partial match bar"; else print "Baz"}' filename
                                                                                              
                                                                                              
                                                                                              
# To sum integers from a file or stdin, one integer per line:
printf '1\n2\n3\n' | awk '{ sum += $1} END {print sum}'

# To use a specific character as separator to sum integers from a file or stdin:
printf '1:2:3' | awk -F ":" '{print $1+$2+$3}'

# To print a multiplication table:
seq 9 | sed 'H;g' | awk -v RS='' '{for(i=1;i<=NF;i++)printf("%dx%d=%d%s", i, NR, i*NR, i==NR?"\n":"\t")}'

# To specify an output separator character:
printf '1 2 3' | awk 'BEGIN {OFS=":"}; {print $1,$2,$3}'
