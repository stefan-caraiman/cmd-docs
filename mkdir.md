# mkdir

create a directory
    mkdir directory

create a directory with all permissions enabled
    mkdir -m 777 unprotected_directory


# Basic Usage

Create a directory:
    mkdir <directory>

# mkdir                                                                                       
                                                                                              
  Creates a directory.                                                                        
                                                                                              
- Create a directory in current directory or given path:                                      
                                                                                              
  mkdir directory                                                                             
                                                                                              
- Create directories recursively (useful for creating nested dirs):                           
                                                                                              
  mkdir -p path/to/directory                                                                  
                                                                                              
                                                                                              
                                                                                              
# To create nested directories:
mkdir -p foo/bar/baz

# To create foo/bar and foo/baz directories:
mkdir -p foo/{bar,baz}

# To create the foo/bar, foo/baz, foo/baz/zip and foo/baz/zap directories:
mkdir -p foo/{bar,baz/{zip,zap}}
