# chmod

`chmod` is used to set read, write or execute permissions on a file.

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
    `chmod <to-whom>+<permissions> <file>`

Remove (`-`) permissions from a file:
    `chmod <from-whom>-<permissions> <file>`


# Flags

Permissions can belong to the owning user (`u`), the group (`g`), and other
people in the world (`o`). All of these at once can be referred to as (`a`).
`ugo` is equivalent to `a`.

Permissions can be read (`r`), write (`w`), and execute (`x`).

Permissions are added with `+` and removed with `-`.


# Adding Permissions

Add execute (`+x`) permissions to the owning user (`u`):

```
    $ ls -l
    total 0
    -rw-r--r--  1 tyrion  group  0 Feb  5 11:40 file.txt
    $ chmod u+x file.txt
    $ ls -l
    total 0
    -rwxr--r--  1 tyrion  group  0 Feb  5 11:40 file.txt
```

# Removing Permissions

Remove read (`-r`) from all permissions holders (`a`). `a-r` is equivalent to
`ugo`:

```
    $ ls -l
    total 0
    -rw-r--r--  1 tyrion  group  0 Feb  5 11:40 file.txt
    $ chmod a-r file.txt
    $ ls -l
    total 0
    --w-------  1 tyrion  group  0 Feb  5 11:40 file.txt
```
                                                     
                                                                              

# Roles
u - user (owner of the file)
g - group (members of file's group)
o - global (all users who are not owner and not part of group)
a - all (all 3 roles above)
