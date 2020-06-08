# uniq

output one copy of each line in input.txt
    uniq input.txt

count occurrences of lines
    uniq -c count.txt

output only lines that are duplicated
    uniq -d repeats.txt

output only the lines that are not repeated in unique.txt
    uniq -u unique.txt

output unique lines ignoring case
    uniq -i case.txt


# Basic Usage

Output a single copy of each unique line in a file:
    uniq <file>

# uniq                                                                                        
                                                                                              
  Output the unique lines from the given input or file.                                       
  Since it does not detect repeated lines unless they are adjacent, we need to sort them first.
                                                                                              
- Display each line once:                                                                     
                                                                                              
  sort file | uniq                                                                            
                                                                                              
- Display only unique lines:                                                                  
                                                                                              
  sort file | uniq -u                                                                         
                                                                                              
- Display only duplicate lines:                                                               
                                                                                              
  sort file | uniq -d                                                                         
                                                                                              
- Display number of occurrences of each line along with that line:                            
                                                                                              
  sort file | uniq -c                                                                         
                                                                                              
- Display number of occurrences of each line, sorted by the most frequent:                    
                                                                                              
  sort file | uniq -c | sort -nr                                                              
                                                                                              
                                                                                              
                                                                                              
# To show all lines without duplication:
# (`sort -u` and `uniq` have the same effect.)
sort <file> | uniq

# To show not duplicated lines:
sort <file> | uniq -u

# To show duplicated lines only:
sort <file> | uniq -d

# To count all lines:
sort <file> | uniq -c

# To count not duplicated lines:
sort <file> | uniq -uc

# To count only duplicated lines:
sort <file> | uniq -dc
