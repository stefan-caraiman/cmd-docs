No entry found for history. Run `eg --list` to see all available entries.
# history                                                                                     
                                                                                              
  Command Line history.                                                                       
                                                                                              
- Display the commands history list with line numbers:                                        
                                                                                              
  history                                                                                     
                                                                                              
- Clear the commands history list (only for current `bash` shell):                            
                                                                                              
  history -c                                                                                  
                                                                                              
- Overwrite history file with history of current `bash` shell (often combined with `history -c` to purge history):
                                                                                              
  history -w                                                                                  
                                                                                              
- Delete the history entry at the specified offset:                                           
                                                                                              
  history -d offset                                                                           
                                                                                              
                                                                                              
                                                                                              
# To see most used top 10 commands:
history | awk '{CMD[$2]++;count++;}END { for (a in CMD)print CMD[a] " " CMD[a]/count*100 "% " a;}' | grep -v "./" | column -c3 -s " " -t | sort -nr | nl | head -n10
