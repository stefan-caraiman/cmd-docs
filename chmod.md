# chmod

give read, write, and execute permissions to everyone
    chmod a+rwx file.txt

remove group write and execute permissions
    chmod g-wx file.txt

give execute permission to the owning user
    chmod u+x file.txt

remove all permissions from non-owning user and non-group members
    chmod o-rwx file.txt


# Basic Usage

Add (`+`) permissions to a file:
    chmod <to-whom>+<permissions> <file>

Remove (`-`) permissions from a file:
    chmod <from-whom>-<permissions> <file>


# Flags

Permissions can belong to the owning user (`u`), the group (`g`), and other
people in the world (`o`). All of these at once can be referred to as (`a`).
`ugo` is equivalent to `a`.

Permissions can be read (`r`), write (`w`), and execute (`x`).

Permissions are added with `+` and removed with `-`.


## Bit Representation

Permissions can also be specified with numbers acting as bit masks. `7` is
`111`, which turns on `rwx`. `777` translates to `111111111`, which turns on
`rwx` for all three permissions holders. `chmod 777` is thus equivalent to
`chmod a+rwx`:
    $ chmod 777 file.txt
    $ ls -l
    total 0
    -rwxrwxrwx  1 tyrion  group  0 Feb  5 11:40 file.txt

`4` is `100`, which corresponds to the read permission. This command will give
read, write, and execute permissions to the owning user, and read permission to
the group and others in the world:
    $ chmod 744 file.txt
    $ ls -l
    total 0
    -rwxr--r--  1 tyrion  group  0 Feb  5 11:40 file.txt


# Adding Permissions

Add execute (`+x`) permissions to the owning user (`u`):
    $ ls -l
    total 0
    -rw-r--r--  1 tyrion  group  0 Feb  5 11:40 file.txt
    $ chmod u+x file.txt
    $ ls -l
    total 0
    -rwxr--r--  1 tyrion  group  0 Feb  5 11:40 file.txt


# Removing Permissions

Remove read (`-r`) from all permissions holders (`a`). `a-r` is equivalent to
`ugo`:
    $ ls -l
    total 0
    -rw-r--r--  1 tyrion  group  0 Feb  5 11:40 file.txt
    $ chmod a-r file.txt
    $ ls -l
    total 0
    --w-------  1 tyrion  group  0 Feb  5 11:40 file.txt

# chmod                                                                                       
                                                                                              
  Change the access permissions of a file or directory.                                       
                                                                                              
- Give the [u]ser who owns a file the right to e[x]ecute it:                                  
                                                                                              
  chmod u+x file                                                                              
                                                                                              
- Give the [u]ser rights to [r]ead and [w]rite to a file/directory:                           
                                                                                              
  chmod u+rw file_or_directory                                                                
                                                                                              
- Remove e[x]ecutable rights from the [g]roup:                                                
                                                                                              
  chmod g-x file                                                                              
                                                                                              
- Give [a]ll users rights to [r]ead and e[x]ecute:                                            
                                                                                              
  chmod a+rx file                                                                             
                                                                                              
- Give [o]thers (not in the file owner's group) the same rights as the [g]roup:               
                                                                                              
  chmod o=g file                                                                              
                                                                                              
- Remove all rights from [o]thers:                                                            
                                                                                              
  chmod o= file                                                                               
                                                                                              
- Change permissions recursively giving [g]roup and [o]thers the abililty to [w]rite:         
                                                                                              
  chmod -R g+w,o+w directory                                                                  
                                                                                              
                                                                                              
                                                                                              
# Add execute for all (myscript.sh)
chmod a+x myscript.sh

# Set user to read/write/execute, group/global to read only (myscript.sh), symbolic mode
chmod u=rwx, go=r myscript.sh 

# Remove write from user/group/global (myscript.sh), symbolic mode
chmod a-w myscript.sh

# Remove read/write/execute from user/group/global (myscript.sh), symbolic mode
chmod = myscript.sh

# Set user to read/write and group/global read (myscript.sh), octal notation
chmod 644 myscript.sh

# Set user to read/write/execute and group/global read/execute (myscript.sh), octal notation
chmod 755 myscript.sh

# Set user/group/global to read/write (myscript.sh), octal notation
chmod 666 myscript.sh

# Roles
u - user (owner of the file)
g - group (members of file's group)
o - global (all users who are not owner and not part of group)
a - all (all 3 roles above)

# Numeric representations
7 - full (rwx)
6 - read and write (rw-)
5 - read and execute (r-x)
4 - read only (r--)
3 - write and execute (-wx)
2 - write only (-w-)
1 - execute only (--x)
0 - none (---)
