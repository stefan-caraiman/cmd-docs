# unzip

unzip a zipped file
    unzip compressed.zip

unzip a zipped file to path/to/output/dir/
    unzip compressed.zip -d path/to/output/dir/


# Basic Usage

Unzip a zipped file:
    unzip <zipped-file>

# unzip                                                                                       
                                                                                              
  Extract compressed files in a ZIP archive.                                                  
                                                                                              
- Extract zip file(s) (for multiple files, separate file paths by spaces):                    
                                                                                              
  unzip file(s)                                                                               
                                                                                              
- Extract zip files(s) to given path:                                                         
                                                                                              
  unzip compressed_file(s) -d /path/to/put/extracted_file(s)                                  
                                                                                              
- List the contents of a zip file without extracting:                                         
                                                                                              
  unzip -l file.zip                                                                           
                                                                                              
- Extract the contents of the file(s) to `stdout` alongside the extracted file names:         
                                                                                              
  unzip -c file.zip                                                                           
                                                                                              
- Extract a zip file created in windows, containing files with non-ascii (chinese) filenames: 
                                                                                              
  unzip -O gbk file.zip                                                                       
                                                                                              
                                                                                              
                                                                                              
# To extract an archive:
unzip <archive>

# To test integrity of archive:
unzip -tq <archive>

# To list files and directories an archive:
unzip -l <archive>
