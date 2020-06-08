# grep

print all lines containing foo in input.txt
    grep "foo" input.txt

print all lines matching the regex "^start" in input.txt
    grep -e "^start" input.txt

print all lines containing bar by recursively searching a directory
    grep -r "bar" directory

print all lines containing bar ignoring case
    grep -i "bAr" input.txt

print 3 lines of context before and after each line matching "foo"
    grep -C 3 "foo" input.txt


# Basic Usage

Search each line in `input_file` for a match against `pattern` and print
matching lines:
    grep "<pattern>" <input_file>


# Find Lines NOT Matching

Print lines that do NOT match a pattern by using the `-v` flag. This will print
all lines that do NOT contain a z (`-v "z"`):
    grep -v "z" input.txt


# Print File Names

Show only the file names containing matches, rather than the matching lines
themselves, by using the `-l` flag:
    grep -r -l "target_pattern" directory

Show only the file names that do NOT contain matches by using the `-L` flag:
    grep -r -L "unwanted_pattern" directory


# Regular Expressions and `egrep`

Regular expressions can be passed to `grep` using the `-e` flag. `egrep` is
equivalent to using the `-e` flag.

The following file is used in the examples:
    $ cat input.txt
    1 2 3
    omega
    alpha foo
    alpha bar
    baz omega
    4 5 6

Match lines beginning (`^`) with `alpha` (`^alpha`):
    $ grep -e "^alpha" input.txt
    alpha foo
    alpha bar

Match lines ending (`$`) with `omega` (`omega$`):
    $ grep -e "omega$" input.txt
    omega
    baz omega

Match any line containing `a` and `o` separated by 0 or more characters (`.*`):
    $ grep -e "a.*o" input.txt
    alpha foo
    baz omega

Match any line containing `z` or `f` (`[zf]`):
    $ grep -e "[zf]" input.txt
    alpha foo
    baz omega

Match any line containing `hello` or `world`:
    $ grep "hello\|world" input.txt
    hello alpha
    omega world

Match all lines with lower case or capital letters a through z (`[a-zA-Z]`):
    $ grep -e "[a-zA-Z]" input.txt
    omega
    alpha foo
    alpha bar
    baz omega

Match all lines containing numbers (`[0-9]`):
    $ grep -e "[0-9]" input.txt
    1 2 3
    4 5 6

Match all lines containing white space (`[[:space:]]`):
    $ grep -e "[[:space:]]" input.txt
    1 2 3
    alpha foo
    alpha bar
    baz omega
    4 5 6

# Fixed Expressions and `fgrep`

`fgrep` is faster than `grep` and `egrep` but only accepts fixed expressions.
This will match lines containing the exact sequence `.*` (`'.*'`). Quoting is
used to prevent shell expansion of the wildcard `*` character:
    fgrep '.*' input.txt


# Searching Compressed Files

`zgrep`, `zegrep`, and `zfgrep` act exactly like `grep`, `egrep`, and `fgrep`,
but they operate on compressed and gzipped files. The same examples shown above
will function with the `z*grep` utilities.

# grep                                                                                        
                                                                                              
  Matches patterns in input text.                                                             
  Supports simple patterns and regular expressions.                                           
                                                                                              
- Search for an exact string:                                                                 
                                                                                              
  grep search_string path/to/file                                                             
                                                                                              
- Search in case-insensitive mode:                                                            
                                                                                              
  grep -i search_string path/to/file                                                          
                                                                                              
- Search recursively (ignoring non-text files) in current directory for an exact string:      
                                                                                              
  grep -RI search_string .                                                                    
                                                                                              
- Use extended regular expressions (supporting `?`, `+`, `{}`, `()` and `|`):                 
                                                                                              
  grep -E ^regex$ path/to/file                                                                
                                                                                              
- Print 3 lines of [C]ontext around, [B]efore, or [A]fter each match:                         
                                                                                              
  grep -C|B|A 3 search_string path/to/file                                                    
                                                                                              
- Print file name with the corresponding line number for each match:                          
                                                                                              
  grep -Hn search_string path/to/file                                                         
                                                                                              
- Use the standard input instead of a file:                                                   
                                                                                              
  cat path/to/file | grep search_string                                                       
                                                                                              
- Invert match for excluding specific strings:                                                
                                                                                              
  grep -v search_string                                                                       
                                                                                              
                                                                                              
                                                                                              
# To search a file for a pattern:
grep <pattern> <file>

# To perform a case-insensitive search (with line numbers):
grep -in <pattern> <file>

# To recursively grep for string <pattern> in <dir>:
grep -R <pattern> <dir>

# Read search patterns from a file (one per line):
grep -f <pattern-file> <file>

# Find lines NOT containing pattern:
grep -v <pattern> <file>

# To grep with regular expressions:
grep "^00" <file>                                               # Match lines starting with 00
grep -E "[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}" <file> # Find IP add

# To find all files that match <pattern> in <dir>
grep -rnw <dir> -e <pattern>

# To exclude grep from your grepped output of ps:
# (Add [] to the first letter. Ex: sshd -> [s]shd)
ps aux | grep '[h]ttpd'

# Colour in red {bash} and keep all other lines
ps aux | grep -E --color 'bash|$'
