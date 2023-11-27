# <span style="color:blue"> Data Compression. </span>

File data is often compressed to save space and reduce the time it takes for
files to be transmitted over the networks.

Linux uses several methods to carry out this compression, including:

| Command | Use                                                                              |
| ------- | -------------------------------------------------------------------------------- |
| gzip    | The most used Linux compression utility                                          |
|         |                                                                                  |
| bzip2   | Produces significantly smaller files than those produced by gzip                 |
|         |                                                                                  |
| xz      | The most space efficient compression utility used in Linux                       |
|         |                                                                                  |
| zip     | Examining and decompressing files from other operating system is often required. |

These techniques vary in terms of compression efficiency (how much space is
saved) and how long they take to compress; in general, more efficient techniques
take longer. Decompression time doesn't vary that much depending on the
different methods.

Additionally, the **tar** utility is often used to group files into one file and
then compress the entire file at once.

### <span style="color:red">gzip</span>

**gzip** is the most used Linux compression utility. It compress very well and
is very fast. The following table provides some usage examples:

| Command          | Use                                                                                                        |
| ---------------- | ---------------------------------------------------------------------------------------------------------- |
| gzip \*          | Compress all files in the current directory; each file is compressed and renamed with a **.gz** extension. |
|                  |                                                                                                            |
| gzip -r projectX | Compress all projectX files, along with all files in all ProjectX directories.                             |
|                  |                                                                                                            |
| gunzip foo       | Uncompress foo, found in the file foo.gz. The **gunzip** command is actually the same as **gzip -d**       |

### <span style="color:red">bzip2</span>

**bzip2** has a similar syntax to **gzip** but uses a different compression
algorithm and produces significantly smaller files, at the price of taking
longer to do its job. Therefore, it's more likely to be used to compress larger
files.

Commonly used examples are also similar to **gzip**:

| Command       | Use                                                                                                                    |
| ------------- | ---------------------------------------------------------------------------------------------------------------------- |
| bzip2 \*      | Compresses all files in the current directory and replaces each file with a renamed file with a **.bz2** extension.    |
|               |                                                                                                                        |
| bunzip2 \*.bz | Uncompress all files with an extension of **.bz2** in the current directory. bunzip2 is equivalent to calling bzip2-d. |

:warning: **NOTE:** bzip2 has recently been deprecated due to lack of
maintenance and the higher compression ratios of **xz** which is still being
actively developed. :warning:

### <span style="color:red">xz</span>

**xz** is the most space-efficient compression utility used in Linux and is used
to store Linux kernel files. Therefore, the compression speed is slower in order
to obtain an even higher compression ratio.

Some examples of use:

| Command                          | Use                                                                                                                 |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| xz \*                            | Compresses all files in the current directory and replaces each file with a renamed file with a **.xz** extension.  |
|                                  |                                                                                                                     |
| xz foo                           | Compress **foo** in **foo.xz** using the default compression level (-6) and removes **foo** if compression suceeds. |
|                                  |                                                                                                                     |
| xz -dk bar.xz                    | Decompresses **bar.xz** to **bar** and doesn't remove **bar.xz** even if decompression is succesful.                |
|                                  |                                                                                                                     |
| xz -dcfa.txt b.txt.xz > abcd.txt | Decompresses a combination of compressed and Uncompressed files to standard output, using a single command.         |
| xz -d \*.xz                      | Decompress compressed files using **xz**                                                                            |

Compressed files are stored with a **.xz** extension.

### <span style="color:red">zip</span>

The **zip** program isn't often used to compress files on Linux, but is often
required to browse and decompress files on other operating systems. Only used on
Linux when you have a compressed file from a Windows user.

| Command             | Use                                                                                          |
| ------------------- | -------------------------------------------------------------------------------------------- |
| zip backup \*       | Compresses all files in the current directory and places them in the **backup.zip**          |
|                     |                                                                                              |
| zip -r backup.zip ~ | Archive the login directory (~) and all files and directories below it in the **backup.zip** |
|                     |                                                                                              |
| unzip backup.zip    | Extracts all files from **backup.zip** and places them in the current directory              |

### <span style="color:red">tar</span>

Historically, **tar** stood for "tape archive" and was used to archive files on magnetic tape. Allows you to create or extract files from a packaged archive,
often called a tarball. At the same time, you can optionally compress it while creating the file and decompress it while extracting its contents.

Here some examples of **tar** usage:

| Command                             |                                             Use                                                                                                        |
|-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| tar xvf mydir.tar                   | Extract all **mydir.tar** files into the **mydir** directory.                                                                                          |
|                                     |                                                                                                                                                        |
| tar zcvf mydir.tar.gz mydir         | Create the file and compress it with **gzip**.                                                                                                         |
|                                     |                                                                                                                                                        | 
| tar jcvf mydir.tar.bz2 mydir        | Create the file and copress with **bz2**.                                                                                                              |
|                                     |                                                                                                                                                        |
| tar Jcvf mydir.tar.xz mydir         | Create the file and compress it with **xz**                                                                                                            |
|                                     |                                                                                                                                                        |
| tar xvf mydir.tar.gz                | Extract all files from **mydir.tar.gz** to the **mydir** directory. :point_right: NOTE: We don't have to tell tar that it's in gzip format.:point_left:|

We can separate the archiving and compression stages, as in:

- tar cvf mydir.tar mydir; gzip mydir.tar
- gunzip mydir.tar.gz; tar xvf mydir.tar

But this is slower and wastes space by creating an unnecessary intermediary **.tar** file.
