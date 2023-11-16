# Comparing files with Diff command.

The **diff** command is used to compare files and directories. This frequently used program has many useful options (queries, man diff) including:

|diff option|                                        Used to                                                                  |
|-----------|-----------------------------------------------------------------------------------------------------------------|
|**-c**     | Provides a list of differences including three lines of context before and after lines that differ in content.  |
|           |                                                                                                                 | 
|**-r**     | Used to recursively compare directories as well as the current directory.                                       |
|           |                                                                                                                 |
|**-i**     | Ignores the case (upper or lower case) of letters.                                                              | 
|           |                                                                                                                 | 
|**-w**     | Ignores differences in spaces and tabs (whitespace).                                                            |
|           |                                                                                                                 |
|**-q**     | Quiet mode: Reports only if files are different whithout listing the differences.                               |
|           |                                                                                                                 |

To compare two files, at the command prompt, type **diff [options] <filename1><filename2>**. diff is intended to be used for text files
for binary files, **cmp** can be used.

If you prefer, there're multiple graphical interfaces for diff, including diffuse, vimdiff and meld.

Here is an example using diffuse:

![diffuse](/home/josemacevo/Documents/Development/linux_course/course_images/diffuse.png)


## Use diff3 and patch

We can compare three files at once using **diff3**, which uses one file as a baseline for the other two. For example, let's say that
both, you and a coworker have made changes to the same file while working independently at the same time. **diff3** can show the
differences based on the common file you both started with. The syntax of diff3 is as follows?

> diff3 <myfile>> <commonfile> <yourfile>

The next example shows the diff3 use:

![diff3](/home/josemacevo/Documents/Development/linux_course/course_images/diff3centos.png)

