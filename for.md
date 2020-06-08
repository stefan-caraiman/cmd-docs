No entry found for for. Run `eg --list` to see all available entries.
# for                                                                                         
                                                                                              
  Shell loop over parameters.                                                                 
                                                                                              
- Perform a command with different arguments:                                                 
                                                                                              
  for argument in 1 2 3; do command $argument; done                                           
                                                                                              
- Perform a command in every directory:                                                       
                                                                                              
  for d in *; do (cd $d; command); done                                                       
                                                                                              
                                                                                              
                                                                                              
# basic loop
for i in 1 2 3 4 5 6 7 8 9 10
do
  echo $i
done

# loop ls command results
for var in `ls -alF`
do
  echo $var
done

# loop over all the JPG files in the current directory
for jpg_file in *.jpg
do
  echo $jpg_file
done

# loop specified number of times
for i in `seq 1 10`
do
  echo $i
done

# same as above, but as one-liner
for i in `seq 1 10`; do echo $i; done

# loop specified number of times: the C/C++ style
for ((i=1;i<=10;++i))
do
  echo $i
done

# loop specified number of times: the brace expansion
for i in {1..10}
do
  echo $i
done