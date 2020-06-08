# cat

show file.txt
    cat file.txt

show file.txt with line numbers
    cat -n file.txt

show file with blank lines squeezed to single space
    cat -s double_spaced.txt


# Basic Usage

Show the input file on `stdout`:
    cat <file>

# cat                                                                                         
                                                                                              
  Print and concatenate files.                                                                
                                                                                              
- Print the contents of a file to the standard output:                                        
                                                                                              
  cat file                                                                                    
                                                                                              
- Concatenate several files into the target file:                                             
                                                                                              
  cat file1 file2 > target_file                                                               
                                                                                              
- Append several files into the target file:                                                  
                                                                                              
  cat file1 file2 >> target_file                                                              
                                                                                              
- Number all output lines:                                                                    
                                                                                              
  cat -n file                                                                                 
                                                                                              
- Display non-printable and whitespace characters (with `M-` prefix if non-ASCII):            
                                                                                              
  cat -v -t -e file                                                                           
                                                                                              
                                                                                              
                                                                                              
# To display the contents of a file:
cat <file>

# To display file contents with line numbers
cat -n <file>

# To display file contents with line numbers (blank lines excluded)
cat -b <file>
