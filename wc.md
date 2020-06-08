# wc

count the lines, words, and bytes in a file
    wc lines_words_bytes.txt

count the lines in a file
    wc -l lines.txt

count the words in a file
    wc -w words.txt

count the bytes in a file
    wc -c bytes.txt

count the characters in a file, supporting unicode etc
    wc -m multi_byte_characters.txt


# Basic Usage

Show the lines and words in a file:
    wc <file>


# Counting Lines and Words

The following file is used in this example:
    $ cat 3words_2lines.txt
    123 567
    89

By default `wc` counts lines, words, and bytes:
    $ wc 3words_2lines.txt
    2       3      11 3words_2lines.txt

This file has 2 lines, 3 words (separated by whitespace), and 11 bytes (the
characters, whitespace, and line endings).

# wc                                                                                          
                                                                                              
  Count lines, words, or bytes.                                                               
                                                                                              
- Count lines in file:                                                                        
                                                                                              
  wc -l file                                                                                  
                                                                                              
- Count words in file:                                                                        
                                                                                              
  wc -w file                                                                                  
                                                                                              
- Count characters (bytes) in file:                                                           
                                                                                              
  wc -c file                                                                                  
                                                                                              
- Count characters in file (taking multi-byte character sets into account):                   
                                                                                              
  wc -m file                                                                                  
                                                                                              
- Use standard input to count lines, words and characters (bytes) in that order:              
                                                                                              
  find . | wc                                                                                 
                                                                                              
                                                                                              
                                                                                              
# To count the number of words (file or STDIN):
wc -w <file>
cat <file> | wc -w

# To count the number of lines (file or STDIN):
wc -l <file>
cat <file> | wc -l

# To count the number of bytes (file or STDIN):
wc -c <file>
cat <file> | wc -c

# To count files and directories at a given location:
ls -l | wc -l

# To if you ever use `wc` in a shell script and need to compare the output with an int you can
# clean the output (wc returns extra characters around the integer) by using xargs:
ls -l | wc -l | xargs
