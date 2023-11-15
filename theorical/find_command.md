# Find command

*Find* is a extremly useful and frequently command used...It recursively traverses the file system tree from any
particular directory or set of directories and locates files that match with the specified conditions. The default
name is always the current working directory.

It's also common to delete files from non-essential or obsolete files in /tmp (and other volatile directories), that
haven't been recently accesed.

When we dont give arguments to find command, this will list all the files in the current directory and all subdirectories
The options frequently ussed to shorted the list are *-name* only show the files with the same name, *-iname* like name
but it not distinguish between upper and lower case and *-type* only show the same type files, like *d* to a directory, 
*l* to symbolic link or *f* to a normal file.

Search examples:

1. find /usr -name gcc -> Searching files and directories whose name is gcc.
2. find /usr -type d -name gcc -> Searching only directories whose name is gcc.
3. find /usr -type f -name gcc -> Searching only normal files whose name is gcc. 

## Advanced search.

*Find* is able to execute commands in files that match with certain search criteria the *-exec* option is used to do that.
To find and delete all files that end in .swp extension:

- find -name "*.swp" -exec rm {} ';'

The {} (squiggly keys) is a marker