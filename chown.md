# chown

change user
    sudo chown username file.txt

change user recursively for all files
    sudo chown -R username directory

change user and group
    sudo chown username:groupname file.txt

change group
    sudo chown :groupname file.txt


# Basic Usage

The caller needs to be a super-user to perform `chown`. Examples are shown
using `sudo`, which is not required if the user is a super-user.

Change the ownership of a file:
    sudo chown <user> <file>

# chown                                                                                       
                                                                                              
  Change user and group ownership of files and directories.                                   
                                                                                              
- Change the owner user of a file/directory:                                                  
                                                                                              
  chown user path/to/file_or_directory                                                        
                                                                                              
- Change the owner user and group of a file/directory:                                        
                                                                                              
  chown user:group path/to/file_or_directory                                                  
                                                                                              
- Recursively change the owner of a directory and its contents:                               
                                                                                              
  chown -R user path/to/directory                                                             
                                                                                              
- Change the owner of a symbolic link:                                                        
                                                                                              
  chown -h user path/to/symlink                                                               
                                                                                              
- Change the owner of a file/directory to match a reference file:                             
                                                                                              
  chown --reference=path/to/reference_file path/to/file_or_directory                          
                                                                                              
                                                                                              
                                                                                              
# To change a file's owner:
chown <user> <file>

# To change a file's owner and group:
chown <user>:<group> <file>

# To change a directory's owner recursively:
chown -R <user> <directory>

# To change ownership to match another file:
chown --reference=<reference-file> <file>
