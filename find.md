# find

files in searchdir named file.txt
    find ./searchdir -name file.txt

only directories in searchdir
    find ./searchdir -type d

show more info
    find ./searchdir -name 'file.txt' -ls


# Basic Usage

Find files and directories matching a given name:
    find <searchdir> -name <name>


# By Name

Search `/searchdir` for files and directories named `file.txt`:
    find ./searchdir -name file.txt


## Case Insensitive

Use `-iname` for case insensitive name searching:
    $ find ./searchdir -iname file.txt
    ./searchdir/file.txt
    ./searchdir/bar/FiLe.TxT


## Wildcards

Wildcards are supported with quotes.

Find files starting with `prefix`:
    $ find ./searchdir -name "prefix*"
    ./searchdir/prefix.txt
    ./searchdir/prefixAndMore.txt


# By Type

## Files only

Will find files (`-type f`) but not directories named `foo`:
    find ./searchdir -type f foo


## Directories and Folders

List only directories by specifying `-type d`:
    $ find ./searchdir -type d -name 'directory'
    ./searchdir/directory


# Size

Use the `-size` flag followed by a number and a unit. Without a unit it matches
blocks.

Find entries exactly two bytes (`-size 2c`). `c` stands for character:
    find ./searchdir -size 2c

Find files exactly 2 kilobytes (`-size 2k`):
    find ./searchdir -size 2k

Find files exactly 2 megabytes (`-size 2M`):
    find ./searchdir -size 2M


## Ranges

Prefix a size with `+` for >= that value and `-` for <= that value.

Find files greater than 5k (`-size +5k`):
    find /dir/to/search +5k

Find files less than 5k (`-size -5k`):
    find /dir/to/search -5k


# Time

Files can also be filtered based on the last time they were changed, modified,
and accessed.

`-ctime` refers to the last time the inode or file was changed, which includes
updating file attributes like owner or permissions as well as file
modifications.

`-mtime` refers to the last time a file was modified.

`-atime` refers to the last time a file was accessed, including by other
command line tools.

Arguments to these flags can be in seconds (`s`), minutes (`m`), hours (`h`),
days (`d`), or weeks (`w`). Preceding an argument with `+` will return files
greater than the condition, while `-` will return files less than the
condition.

Find files modified (`-mtime`) less than 20 minutes (`-20m`) ago:
    find /searchdir -mtime -20m

Find files last accessed (`-atime`) more than 2 weeks (`+2w`) ago:
    find /searchdir -atime -w2

Alternatively, you can return files that have been modified more recently than
another file with `-newer`:
    find /searchdir -newer other.txt


# Depth

Find files and directories only two levels deep (`-depth 2` or `-d 2`):
    $ find ./one -depth 2
    ./one/two
    ./one/foo.txt

Find only files (`-type f`) >= two levels (`-mindepth 2`) and <= three levels
(`-maxdepth 3`) deep:
    $ find ./one -type f -mindepth 2 -maxdepth 3
    ./one/twoLevels.txt
    ./one/two/threeLevels.txt


# Boolean Operators

Flags are ANDed by default, but can also achieve OR and NOT functionality.

## AND

List files greater bigger than 500k (`+500k`) and named `bigFile.txt`
(`-name bigFile.txt`). These two commands are equivalent:
    $ find ./searchdir -size +500k -name bigFile.txt
    $ find ./searchdir -size +500k -and -name bigFile.txt

## OR

List files bigger than 500k (`+500k`) or those that are named `smallFile.txt`
(`-or -name smallFile.txt`):
    find ./searchdir -size +500k -or -name smallFile.txt

## NOT

List files bigger than 50 megabytes (`-size +50M`) that are not named
`unwanted.txt` (`-not -name unwanted.txt`):
    find ./searchdir -size +50M ! -name unwanted.txt


# Execute Commands on Results

You can execute a command on all matched files using the `-exec` option. The
string `{}` will be replaced with the name of the matched file, and the command
must be terminated with an escaped semicolon (`\;`).

## Change Permissions

Give all files (`-type f`) 755 permissions (`-exec chmod 755 '{}' \;`):
    find ./searchdir -type f -exec chmod 755 '{}' \;

## Delete

Deleting files has its own flag. Find all files (`-type f`) ending with a tilde
(`-name '*~'`) and remove them (`-delete`):
    find ./searchdir -type f -name '*~' -delete

# find                                                                                        
                                                                                              
  Find files or directories under the given directory tree, recursively.                      
                                                                                              
- Find files by extension:                                                                    
                                                                                              
  find root_path -name '*.ext'                                                                
                                                                                              
- Find files by matching multiple patterns:                                                   
                                                                                              
  find root_path -name '*pattern_1*' -or -name '*pattern_2*'                                  
                                                                                              
- Find directories matching a given name, in case-insensitive mode:                           
                                                                                              
  find root_path -type d -iname '*lib*'                                                       
                                                                                              
- Find files matching a path pattern:                                                         
                                                                                              
  find root_path -path '**/lib/**/*.ext'                                                      
                                                                                              
- Find files matching a given pattern, excluding specific paths:                              
                                                                                              
  find root_path -name '*.py' -not -path '*/site-packages/*'                                  
                                                                                              
- Find files matching a given size range:                                                     
                                                                                              
  find root_path -size +500k -size -10M                                                       
                                                                                              
- Run a command for each file (use `{}` within the command to access the filename):           
                                                                                              
  find root_path -name '*.ext' -exec wc -l {} \;                                              
                                                                                              
- Find files modified in the last 7 days, and delete them:                                    
                                                                                              
  find root_path -mtime -7 -delete                                                            
                                                                                              
                                                                                              
                                                                                              
# To find files by case-insensitive extension (ex: .jpg, .JPG, .jpG):
find . -iname "*.jpg"

# To find directories:
find . -type d

# To find files:
find . -type f

# To find files by octal permission:
find . -type f -perm 777

# To find files with setuid bit set:
find . -xdev \( -perm -4000 \) -type f -print0 | xargs -0 ls -l

# To find files with extension '.txt' and remove them:
find ./path/ -name '*.txt' -exec rm '{}' \;

# To find files with extension '.txt' and look for a string into them:
find ./path/ -name '*.txt' | xargs grep 'string'

# To find files with size bigger than 5 Mebibyte and sort them by size:
find . -size +5M -type f -print0 | xargs -0 ls -Ssh | sort -z

# To find files bigger than 2 Megabyte and list them:
find . -type f -size +200000000c -exec ls -lh {} \; | awk '{ print $9 ": " $5 }'

# To find files modified more than 7 days ago and list file information:
find . -type f -mtime +7d -ls

# To find symlinks owned by a user and list file information:
find . -type l -user <username-or-userid> -ls

# To search for and delete empty directories:
find . -type d -empty -exec rmdir {} \;

# To search for directories named build at a max depth of 2 directories:
find . -maxdepth 2 -name build -type d

# To search all files who are not in .git directory:
find . ! -iwholename '*.git*' -type f

# To find all files that have the same node (hard link) as MY_FILE_HERE:
find . -type f -samefile MY_FILE_HERE 2>/dev/null

# To find all files in the current directory and modify their permissions:
find . -type f -exec chmod 644 {} \;
