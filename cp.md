# cp

copy a file
    cp original.txt copy.txt

copy a directory
    cp -R directory directory_copy

prompt if will overwrite existing file
    cp -i foo.txt directoryWithFoo/


# Basic Usage

Copy a file:
    cp <original_file> <copied_file>

Copy a directory using the recursive (`-R`) flag:
    cp -R <original_directory> <copied_directory>


# Directories

Behavior differs if the argument that is the directory being copied ends with a
`/`. If it does end with a `/` the contents are copied as opposed to the
directory itself. For example, `cp -R foo/ bar` will take the contents of the
`foo` directory and copy them into `bar`, while `cp -R foo bar` will copy `foo`
itself and put it into `bar`.

# cp                                                                                          
                                                                                              
  Copy files and directories.                                                                 
                                                                                              
- Copy a file to another location:                                                            
                                                                                              
  cp path/to/file.ext path/to/copy.ext                                                        
                                                                                              
- Copy a file into another directory, keeping the filename:                                   
                                                                                              
  cp path/to/file.ext path/to/target_parent_directory                                         
                                                                                              
- Recursively copy a directory's contents to another location (if the destination exists, the directory is copied inside it):
                                                                                              
  cp -r path/to/directory path/to/copy                                                        
                                                                                              
- Copy a directory recursively, in verbose mode (shows files as they are copied):             
                                                                                              
  cp -vr path/to/directory path/to/copy                                                       
                                                                                              
- Copy text files to another location, in interactive mode (prompts user before overwriting): 
                                                                                              
  cp -i *.txt path/to/target_directory                                                        
                                                                                              
- Dereference symbolic links before copying:                                                  
                                                                                              
  cp -L link path/to/copy                                                                     
                                                                                              
- Use the full path of source files, creating any missing intermediate directories when copying:
                                                                                              
  cp --parents source/path/to/file path/to/copy                                               
                                                                                              
                                                                                              
                                                                                              
# To copy a file:
cp ~/Desktop/foo.txt ~/Downloads/foo.txt

# To copy a directory:
cp -r ~/Desktop/cruise_pics/ ~/Pictures/

# To create a copy but ask to overwrite if the destination file already exists:
cp -i ~/Desktop/foo.txt ~/Documents/foo.txt

# To create a backup file with date:
cp foo.txt{,."$(date +%Y%m%d-%H%M%S)"}
