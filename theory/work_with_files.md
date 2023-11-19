# Work with files and directories.

We're going how to do basic operations with files in a centos eight stream, should be the same in any other linux system.
The first step is create two files, they can be empties or to have little content.
The first way to do that is using the ECHO command, that is echo follows the greater than simbol (>) and the file name:
echo > file1 for example.
The second way to do that is using the TOUCH command that is touch and the file name: touch file2 for example.
Now if I do ls -l file1 file2 we can see that have been created two very small files at the same time.
If I want change the name of one of them I could do it using the MOVE command (MV) that's mv file1 file1-newname.
Then if I do ls -l \*file* I can see the file with the new name, if I want to eliminte it I can just do rm file2.
And that is all that we need, however is a good idea use the (-i) option to interactuate when we want to delete files or directories.
rm -i file1-newname and it ask me if I want to delete the file, to much distributions are configurated with the -i option by default so that
you always have the option to change your mind about delete something before to do that.

### How to create a directory.
I could do mkdir directory1, in fact I can create more than one directory on the same line, I can do mkdir dir1 dir2 dir3 if I look now 
I can see that I have three empty directories with diferent names.
I'm goint to create two files in one of the directories I can do that writing touch dir2/file1 and touch dir2/file2, now I can do ls -lR dir*
and I can see that the job is done.
dir1 is empty, dir2 has this two files and dir3 is empty too.
To eliminate directories the command is rmdir *, if I do this we can observe that dir1 and dir3 was eliminated but dir2 is present, because
isn't an empty directory, if we need delete dir2 we need to do rm -rf dir2 and now the directory and all its files were deleted.

### **Be carefull** with the rm -rf command because if you use it in the wrong way you could destroy your system.

### Command Resume:

1. **echo > new_file** -> Create a new file.
2. **touch new_file2** -> Crete a new file.
3. **ls -l new_file new_file2** -> See created files.
4. **mv new_file new_fileb** -> Change the file name.
5. **ls -l \*file*** -> See created files.
6. **rm new_file2** -> Delete file2.
7. **rm -i new_file2** -> Delete file2 interactively.
8. **mkdir dir1** -> Create a directory.
9. **mkdir dir1 dir2 dir3 dir4** -> Create many directories at the same time in the same line.
10. **touch dir2/file1** -> Create a file inside dir2 directory.
11. **ls -lR dir \*** -> See files inside the current directory.
12. **rmdir \*** -> Eliminate all empty directories.
13. **rm -rf dir2**-> Eliminate the dir2 directory empty or not.
14. **rm -rf \*** -> Eliminate all directories.
