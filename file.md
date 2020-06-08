# file

determine the file type of foo.txt
    file foo.txt

keep going and show all the matching file types, not just the first
    file -k index.html

show type by looking inside compressed files
    file -z compressed.gzip

try to classify special files like disk partitions
    file -s /dev/disk0


# Basic Usage

Determine the type of a file:
    file <file>

# file                                                                                        
                                                                                              
  Determine file type.                                                                        
                                                                                              
- Give a description of the type of the specified file. Works fine for files with no file extension:
                                                                                              
  file filename                                                                               
                                                                                              
- Look inside a zipped file and determine the file type(s) inside:                            
                                                                                              
  file -z foo.zip                                                                             
                                                                                              
- Allow file to work with special or device files:                                            
                                                                                              
  file -s filename                                                                            
                                                                                              
- Don't stop at first file type match; keep going until the end of the file:                  
                                                                                              
  file -k filename                                                                            
                                                                                              
- Determine the mime encoding type of a file:                                                 
                                                                                              
  file -i filename                                                                            
                                                                                              
                                                                                              
                                                                                              
No cheatsheet found for 'file'.
