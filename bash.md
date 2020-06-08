No entry found for bash. Run `eg --list` to see all available entries.
# bash                                                                                        
                                                                                              
  Bourne-Again SHell.                                                                         
  `sh`-compatible command line interpreter.                                                   
  More information: <https://gnu.org/software/bash>.                                          
                                                                                              
- Start interactive shell:                                                                    
                                                                                              
  bash                                                                                        
                                                                                              
- Execute a command:                                                                          
                                                                                              
  bash -c "command"                                                                           
                                                                                              
- Run commands from a file:                                                                   
                                                                                              
  bash file.sh                                                                                
                                                                                              
- Run commands from a file, logging all commands executed to the terminal:                    
                                                                                              
  bash -x file.sh                                                                             
                                                                                              
- Run commands from a file, stopping at the first error:                                      
                                                                                              
  bash -e file.sh                                                                             
                                                                                              
- Run commands from `stdin`:                                                                  
                                                                                              
  bash -s                                                                                     
                                                                                              
- Print the version information of bash (use `echo $BASH_VERSION` to show just the version string):
                                                                                              
  bash --version                                                                              
                                                                                              
                                                                                              
                                                                                              
# To implement a for loop:
for file in *;
do 
    echo $file found;
done

# To implement a case command:
case "$1"
in
    0) echo "zero found";;
    1) echo "one found";;
    2) echo "two found";;
    3*) echo "something beginning with 3 found";;
esac

# To turn on debugging:
set -x

# To turn off debugging:
set +x

# Retrieve N-th piped command exit status:
printf 'foo' | fgrep 'foo' | sed 's/foo/bar/'
echo ${PIPESTATUS[0]}  # replace 0 with N

# To create a lockfile:
( set -o noclobber; echo > my.lock ) || echo 'Failed to create lock file'
