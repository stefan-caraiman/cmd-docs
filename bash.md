# bash                                                                                        
                                                                                              
Bourne-Again SHell - BASH is a Linux shell and a scripting language.       

Bash is the default **shell/terminal** on most Linux distributions.

# Basic Usage

## Start a Bash shell:                                                                    
                                                                                              
`bash`                                                                                     
                                                                                              
## Execute a command:                                                                          
                                                                                              
`bash -c "command"`                                                                   
                                                                                              
## Run commands from a file:                                                                   
                                                                                              
`bash file.sh`                                                                           


## To implement a for loop:

```
for file in ls;
do 
    echo "$file found";
done
```

## To turn on debugging and see what commands run in a bash script:

`set -x`

## To turn off debugging in bash:

`set +x`
