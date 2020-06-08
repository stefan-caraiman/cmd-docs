# ps

show all processes
    ps -ef

show process with id 37
    ps -p 37

show all processes with verbose information, including memory and CPU usage
    ps -ev

show processes belonging to user tyrion
    ps -u tyrion

show all threads
    ps -efM


# Basic Usage

Print processes for all users (`-e`) with a more detailed format (`-f`):
    ps -ef

`ps` can be more usable if you pipe it to `less`:
    ps -ef | less

Print all processes belonging to a specific user (`-u`):
    ps -u <username>


# Showing Detailed Information

Print verbose output for all (`-e`) processes with both memory and CPU usage
(`-v`), as well as the extended information provided by `-f`:
    ps -evf


# Finding by Process Name

This command uses `ps` to show all processes (`-e`) that Google Chrome
(`grep "Google Chrome"`) is running:
    ps -e | grep "Google Chrome"

# ps                                                                                          
                                                                                              
  Information about running processes.                                                        
                                                                                              
- List all running processes:                                                                 
                                                                                              
  ps aux                                                                                      
                                                                                              
- List all running processes including the full command string:                               
                                                                                              
  ps auxww                                                                                    
                                                                                              
- Search for a process that matches a string:                                                 
                                                                                              
  ps aux | grep string                                                                        
                                                                                              
- List all processes of the current user in extra full format:                                
                                                                                              
  ps --user $(id -u) -F                                                                       
                                                                                              
- List all processes of the current user as a tree:                                           
                                                                                              
  ps --user $(id -u) f                                                                        
                                                                                              
- Get the parent pid of a process:                                                            
                                                                                              
  ps -o ppid= -p pid                                                                          
                                                                                              
                                                                                              
                                                                                              
# To list every process on the system:
ps aux

# To list a process tree:
ps axjf

# To list every process owned by foouser:
ps -aufoouser

# To list every process with a user-defined format:
ps -eo pid,user,command

# Exclude grep from your grepped output of ps.
# Add [] to the first letter. Ex: sshd -> [s]shd
ps aux | grep '[h]ttpd'
