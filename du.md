# du

show size of foo.txt in human readable units
    du -h foo.txt

show size of directory in human readable units without listing contents
    du -sh directory


# Basic Usage

Show the size on disk in human readable units, as opposed to blocks:
    du -h <file>


## Sort by Human-Readable Size on Disk

By default `du` displays file size in blocks. This allows easy sorting by
piping to `sort`:
    du <files> | sort

However, this will fail when the `-h` flag is used to show disk usage in
human-readable units, as 1G is lexicographically before 1M, even though 1M is
smaller than 1G. This can be overcome by system-dependent usage of the `sort`
command.


### Linux

Sort by size on disk in human readable units (`-h`):
    du -h <files> | sort -h


### OSX

On OSX, the `coreutils` package will be necessary. Install it with:
    brew install coreutils

After having it installed, the `gsort` command will be available, which can
sort by human readable units (`-h`):
    du -h <files> | gsort -h

# du                                                                                          
                                                                                              
  Disk usage: estimate and summarize file and directory space usage.                          
                                                                                              
- List the sizes of a directory and any subdirectories, in the given unit (B/KB/MB):          
                                                                                              
  du -b|k|m path/to/directory                                                                 
                                                                                              
- List the sizes of a directory and any subdirectories, in human-readable form (i.e. auto-selecting the appropriate unit for each size):
                                                                                              
  du -h path/to/directory                                                                     
                                                                                              
- Show the size of a single directory, in human readable units:                               
                                                                                              
  du -sh path/to/directory                                                                    
                                                                                              
- List the human-readable sizes of a directory and of all the files and directories within it:
                                                                                              
  du -ah path/to/directory                                                                    
                                                                                              
- List the human-readable sizes of a directory and any subdirectories, up to N levels deep:   
                                                                                              
  du -h --max-depth=N path/to/directory                                                       
                                                                                              
- List the human-readable size of all .jpg files in subdirectories of the current directory, and show a cumulative total at the end:
                                                                                              
  du -ch */*.jpg                                                                              
                                                                                              
                                                                                              
                                                                                              
# To sort directories/files by size:
du -sk *| sort -rn

# To show cumulative human-readable size:
du -sh
