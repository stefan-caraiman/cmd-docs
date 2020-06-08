# sudo

execute ls as the super user
    sudo ls

execute ls as the user tyrion
    sudo -u tyrion ls


# Basic Usage

Execute a command as the super-user:
    sudo <command>

Execute a command as another user:
    sudo -u <user> <command>

# sudo                                                                                        
                                                                                              
  Executes a single command as the superuser or another user.                                 
                                                                                              
- Run a command as the superuser:                                                             
                                                                                              
  sudo less /var/log/syslog                                                                   
                                                                                              
- Edit a file as the superuser with your default editor:                                      
                                                                                              
  sudo -e /etc/fstab                                                                          
                                                                                              
- Run a command as another user and/or group:                                                 
                                                                                              
  sudo -u user -g group id -a                                                                 
                                                                                              
- Repeat the last command prefixed with "sudo" (only in bash, zsh, etc.):                     
                                                                                              
  sudo !!                                                                                     
                                                                                              
- Launch the default shell with superuser privileges:                                         
                                                                                              
  sudo -i                                                                                     
                                                                                              
                                                                                              
                                                                                              
No cheatsheet found for 'sudo'.
