# <span style="color:blue"> File utility, how to use it.</span>

On Linux, a file's extension often doesn't identify what type of file is, as it might on other operating systems.
You can't assume that a file named *file.txt* is a text file and not an executable program. In Linux, a file name 
is usually more meaningful to the user of the system than to the system itself. In fact, most applications directly
examine the contents of a file to see what type of object it is rather than relying on an extension. This is very
different from the way Windows handles file names, where a file name ending with *.exe*, for example, represents
an executable binary file.

The actual nature of a file can be determined using the file utility. For file names given as arguments, it examines
the content and certain characteristics to determine whether the files are plain text, shared libraries, executable
programs, scripts, or something else.

![](/home/josemacevo/Documents/Development/linux_course/course_images/fileutil.png)


