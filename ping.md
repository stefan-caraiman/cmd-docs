# ping

check if www.google.com is reachable
    ping www.google.com

stop pinging after 10 seconds
    ping -w 10 www.google.com

wait 3 seconds between packets
    ping -i 3 www.google.com

send only 2 packets then stop
    ping -c 2 www.google.com

send a packet size of 10 bytes instead of the default 56
    ping -s 10 www.google.com


# Basic Usage

Use the ICMP protocol to check if a host is reachable:
    ping <host>

By default `ping` sends 56 bytes in a packet plus 8 bytes of header, for a
total of 64 bytes. This can be adjusted with the size (`-s`) option:
    ping -s <size> <host>

Use `<CTRL>-c` to stop `ping`.

# ping                                                                                        
                                                                                              
  Send ICMP ECHO_REQUEST packets to network hosts.                                            
                                                                                              
- Ping host:                                                                                  
                                                                                              
  ping host                                                                                   
                                                                                              
- Ping a host only a specific number of times:                                                
                                                                                              
  ping -c count host                                                                          
                                                                                              
- Ping host, specifying the interval in seconds between requests (default is 1 second):       
                                                                                              
  ping -i seconds host                                                                        
                                                                                              
- Ping host without trying to lookup symbolic names for addresses:                            
                                                                                              
  ping -n host                                                                                
                                                                                              
- Ping host and ring the bell when a packet is received (if your terminal supports it):       
                                                                                              
  ping -a host                                                                                
                                                                                              
- Also display a message if no response was received:                                         
                                                                                              
  ping -O host                                                                                
                                                                                              
                                                                                              
                                                                                              
# To ping <host> with 15 packets:
ping -c 15 <host>

# To ping <host> with 15 packets, one every .5 seconds:
ping -c 15 -i .5 <host>

# To test if a packet size of 1500 bytes is supported (to check the MTU for example):
ping -s 1500 -c 10 -M do <host>
