No entry found for ssh. Run `eg --list` to see all available entries.
# ssh                                                                                         
                                                                                              
  Secure Shell is a protocol used to securely log onto remote systems.                        
  It can be used for logging or executing commands on a remote server.                        
                                                                                              
- Connect to a remote server:                                                                 
                                                                                              
  ssh username@remote_host                                                                    
                                                                                              
- Connect to a remote server with a specific identity (private key):                          
                                                                                              
  ssh -i path/to/key_file username@remote_host                                                
                                                                                              
- Connect to a remote server using a specific port:                                           
                                                                                              
  ssh username@remote_host -p 2222                                                            
                                                                                              
- Run a command on a remote server:                                                           
                                                                                              
  ssh remote_host command -with -flags                                                        
                                                                                              
- SSH tunneling: Dynamic port forwarding (SOCKS proxy on localhost:9999):                     
                                                                                              
  ssh -D 9999 -C username@remote_host                                                         
                                                                                              
- SSH tunneling: Forward a specific port (localhost:9999 to example.org:80) along with disabling pseudo-[t]ty allocation and executio[n] of remote commands:
                                                                                              
  ssh -L 9999:example.org:80 -N -T username@remote_host                                       
                                                                                              
- SSH jumping: Connect through a jumphost to a remote server (Multiple jump hops may be specified separated by comma characters):
                                                                                              
  ssh -J username@jump_host username@remote_host                                              
                                                                                              
- Agent forwarding: Forward the authentication information to the remote machine (see `man ssh_config` for available options):
                                                                                              
  ssh -A username@remote_host                                                                 
                                                                                              
                                                                                              
                                                                                              
# To ssh via pem file (which normally needs 0600 permissions):
ssh -i <pemfile> <user>@<host>

# To connect on a non-standard port:
ssh -p <port> <user>@<host>

# To connect and forward the authentication agent:
ssh -A <user>@<host>

# To execute a command on a remote server:
ssh -t <user>@<host> 'the-remote-command'

# To tunnel an x session over SSH:
ssh -X <user>@<host>

# Redirect traffic with a tunnel between local host (port 8080) and a remote
# host (remote.example.com:5000) through a proxy (personal.server.com):
ssh -f -L 8080:remote.example.com:5000 user@personal.server.com -N

# To launch a specific x application over SSH:
ssh -X -t <user>@<host> 'chromium-browser'

# To create a SOCKS proxy on localhost and <port>:
ssh -qND <port> <user>@<host>

# To tunnel an ssh session over the SOCKS proxy on localhost and port 9999:
ssh -o "ProxyCommand nc -x 127.0.0.1:9999 -X 4 %h %p" <user>@<host>

# -X use an xsession, -C compress data, "-c blowfish" use the encryption blowfish:
ssh <user>@<host> -C -c blowfish -X

# For more information, see:
# http://unix.stackexchange.com/q/12755/44856

# To copy files and folders through ssh from remote host to pwd with tar.gz
# compression when there is no rsync command available:
ssh <user>@<host> "cd /var/www/Shared/; tar zcf - asset1 asset2" | tar zxf -

# To mount folder/filesystem through SSH
# Install SSHFS from https://github.com/libfuse/sshfs
# Will allow you to mount a folder securely over a network.
sshfs <user>@<host>:/path/to/folder /path/to/mount/point

# Emacs can read file through SSH
# Doc: http://www.gnu.org/software/emacs/manual/html_node/emacs/Remote-Files.html
emacs /ssh:<user>@<host>:<file>
