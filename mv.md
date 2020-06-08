# mv

rename a file
    mv old_name.txt new_name.txt

move a file to a different directory
    mv foo.txt new_location/foo.txt

move a file but prompt before overwriting
    mv -i foo.txt dirWithFoo/


# Basic Usage

`mv` lets you rename and move files:
    mv <old_location> <new_location>

# mv                                                                                          
                                                                                              
  Move or rename files and directories.                                                       
                                                                                              
- Move files in arbitrary locations:                                                          
                                                                                              
  mv source target                                                                            
                                                                                              
- Do not prompt for confirmation before overwriting existing files:                           
                                                                                              
  mv -f source target                                                                         
                                                                                              
- Prompt for confirmation before overwriting existing files, regardless of file permissions:  
                                                                                              
  mv -i source target                                                                         
                                                                                              
- Do not overwrite existing files at the target:                                              
                                                                                              
  mv -n source target                                                                         
                                                                                              
- Move files in verbose mode, showing files after they are moved:                             
                                                                                              
  mv -v source target                                                                         
                                                                                              
                                                                                              
                                                                                              
# To move a file from one place to another:
mv <src> <dest>

# To move a file from one place to another and automatically overwrite if the destination file exists:
# (This will override any previous -i or -n args)
mv -f <src> <dest>

# To move a file from one place to another but ask before overwriting an existing file:
# (This will override any previous -f or -n args)
mv -i <src> <dest>

# To move a file from one place to another but never overwrite anything:
# (This will override any previous -f or -i args)
mv -n <src> <dest>

# To move listed file(s) to a directory
mv -t <dest> <file>...
