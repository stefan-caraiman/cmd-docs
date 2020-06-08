# ifconfig

display information about network interfaces
    ifconfig

display MAC addresses
    ifconfig | grep ether

set a new MAC address to en0
    sudo ifconfig en0 ether aa:bb:cc:dd:ee:ff

display local IP addresses
    ifconfig | grep 'inet ' | grep -v '127.0.0.1' | cut -d' ' -f2


# Basic Usage

Display basic information:
    ifconfig

Set network parameters:
    sudo ifconfig <interface> <family> <new_address>

# ifconfig                                                                                    
                                                                                              
  Network Interface Configurator.                                                             
                                                                                              
- View network settings of an ethernet adapter:                                               
                                                                                              
  ifconfig eth0                                                                               
                                                                                              
- Display details of all interfaces, including disabled interfaces:                           
                                                                                              
  ifconfig -a                                                                                 
                                                                                              
- Disable eth0 interface:                                                                     
                                                                                              
  ifconfig eth0 down                                                                          
                                                                                              
- Enable eth0 interface:                                                                      
                                                                                              
  ifconfig eth0 up                                                                            
                                                                                              
- Assign IP address to eth0 interface:                                                        
                                                                                              
  ifconfig eth0 ip_address                                                                    
                                                                                              
                                                                                              
                                                                                              
# To display network settings of an interface:
ifconfig <interface>

# To display all interfaces, even if down:
ifconfig -a

# To take down / up the wireless adapter:
ifconfig wlan0 {up|down} 

# To set a static IP and netmask:
ifconfig eth0 192.168.1.100 netmask 255.255.255.0

# You may also need to add a gateway IP:
route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1
