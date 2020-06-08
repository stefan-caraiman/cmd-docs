# rm

delete a file
    rm file.txt

delete a directory and its contents
    rm -r directory


# Basic Usage

Remove a file from the file system:
    rm <file>

Remove a directory with the recursive (`-r`) flag:
    rm -r <directory>

# rm                                                                                          
                                                                                              
  Remove files or directories.                                                                
                                                                                              
- Remove files from arbitrary locations:                                                      
                                                                                              
  rm path/to/file path/to/another/file                                                        
                                                                                              
- Recursively remove a directory and all its subdirectories:                                  
                                                                                              
  rm -r path/to/directory                                                                     
                                                                                              
- Forcibly remove a directory, without prompting for confirmation or showing error messages:  
                                                                                              
  rm -rf path/to/directory                                                                    
                                                                                              
- Interactively remove multiple files, with a prompt before every removal:                    
                                                                                              
  rm -i file(s)                                                                               
                                                                                              
- Remove files in verbose mode, printing a message for each removed file:                     
                                                                                              
  rm -v path/to/directory/*                                                                   
                                                                                              
                                                                                              
                                                                                              
# To remove all files and subdirs in <dir>:
rm -rf <dir>

# To ignore non-existent files:
rm -f <dir>

# To remove a file with this inode:
find /tmp/ -inum 6666 -exec rm -i '{}' \;
