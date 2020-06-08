# nc

receive input on port 1337
    nc -l 1337

receive input on port 1337 on GNU nc implementation
    nc -l -p 1337

receive input on port 1337 without hanging up after a connection
    nc -k -l 1337

send a file to the address 192.168.1.42 on port 1337
    cat file | nc 192.168.1.42 1337

send a file to the address 192.168.1.42 on port 1337 with progress
    pv file | nc 192.168.1.42 1337

check if 127.0.0.1 is listening on port 80 but do not connect
    nc -vz 127.0.0.1 80


# Basic Usage

Send what is read from stdin to an address and a port:
    nc <address> <port>

Send what is read from stdin to an address and a port on the GNU implementation
of `nc`:
    nc <address> -p <port>

Listen on a port and send it to stdout:
    nc -l <port>

Listen on a port and send it to stdout on the GNU implementation of `nc`:
    nc -l -p <port>


# Compatibility

Usage for `nc`, or `netcat`, varies highly depending on your system. Some
implementations require both the `-l` and `-p` flags to listen on a port, for
instance, whereas others explicitly list using the `-l` and `-p` flags together
is an error. Use these examples as a starting point, but turn to `man` for the
specifics of your implementation.

# nc                                                                                          
                                                                                              
  Netcat is a versatile utility for working with TCP or UDP data.                             
  More information: <https://nmap.org/ncat>.                                                  
                                                                                              
- Listen on a specified port and print any data received:                                     
                                                                                              
  nc -l port                                                                                  
                                                                                              
- Connect to a certain port (you can then write to this port):                                
                                                                                              
  nc ip_address port                                                                          
                                                                                              
- Set a timeout:                                                                              
                                                                                              
  nc -w timeout_in_seconds ipaddress port                                                     
                                                                                              
- Serve a file:                                                                               
                                                                                              
  nc -l port < file                                                                           
                                                                                              
- Receive a file:                                                                             
                                                                                              
  nc ip_address port > file                                                                   
                                                                                              
- Server stay up after client detach:                                                         
                                                                                              
  nc -k -l port                                                                               
                                                                                              
- Client stay up after EOF:                                                                   
                                                                                              
  nc -q timeout ip_address                                                                    
                                                                                              
- Scan the open ports of a specified host:                                                    
                                                                                              
  nc -v -z ip_address port                                                                    
                                                                                              
- Act as proxy and forward data from a local TCP port to the given remote host:               
                                                                                              
  nc -l local_port | nc hostname remote_port                                                  
                                                                                              
                                                                                              
                                                                                              
# To open a TCP connection from <src-port> to <dest-port> of <dest-host>, with a timeout of <seconds>
nc -p <src-port> -w <seconds> <dest-host> <dest-port>

# To open a UDP connection to <dest-port> of <dest-host>:
nc -u <dest-host> <dest-port>

# To open a TCP connection to port 42 of <host> using <source-host> as the IP for the local end of the connection:
nc -s <source-host> <dest-host> <port>

# To create and listen on a UNIX-domain stream socket:
nc -lU /var/tmp/dsocket

# To connect to <dest-port> of <dest-host> via an HTTP proxy at <proxy-host>,
# <proxy-port>. This example could also be used by ssh(1); see the ProxyCommand
# directive in ssh_config(5) for more information.
nc -x<proxy-host>:<proxy-port> -Xconnect <dest-host> <dest-port>

# The same example again, this time enabling proxy authentication with username "ruser" if the proxy requires it:
nc -x<proxy-host>:<proxy-port> -Xconnect -Pruser <host> <port>

# To choose the source IP for the testing using the -s option
nc -zv -s source_IP target_IP Port
