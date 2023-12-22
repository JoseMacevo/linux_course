# <span style="color:blue"> dd command practice. </span>

Archiving (or backing up) your files from time to time is essentially a good
practice. We can type a command and thereby unintentionally crush the files
that you need and didn't intend to alter.

Aditinaly, while your hardware may be considered faily reliable, all devices
fail in some way at some point (even if it's just an unexpected power failure).
This often happens at the worst possible time. Making regular backups of files
is a good habit.

Of course, it's important to back up to external systems over a network or to
external storage, such as an external drive or USB stick. Here, we'll make a
back up file on the same system, which is very useful, but won't help if the
drive fails catastrophically, or the computer is stolen, or the building is 
wiped out by an asteroid or fire.

1. First of all, we're going to use **tar** to create a backup that all files
   and directories of our main directories. We're going to place the result
   **tarball file** in the **/tmp** directory, naming it *backup.tar*.
   
   *Solution:*

   > student:/tmp>tar -cvf /tmp/backup.tar ~
   
   *or:*

   > student:/tmp>tar -cvf /tmp/backupt.tar /home/student

2. Second, perform the same task with **gzip** compression using the **-z** option
   to **tar**, creating **/tmp/backup.tar.gz.
 
   *Solution:*
    
    (Note that we may have omitted **-** in the unchanged options. In the following
    we'll make it so you don't bother using the **-v** option for verbose. To create
    files with the three compression utilities)
   
   - student:/tmp>tar zcf /tmp/backup.tar.gz ~
   - student:/tmp>tar jcf /tmp/backup.tar.bz2 ~
   - student:/tmp>tar Jcf /tmp/backup.tar.xz ~


3. Compare the size of two files(with **ls-l** first using **-h** to make it human readable).
   
   - student:/tmp>ls -lh /tmp/backup*
     - -rw-rw-r-- 1 student student 8.3M Apr 17 10:14 /tmp/backup2.tar.gz
     - -rw-rw-r-- 1 student student 12M Apr 17 10:13 /tmp/backup.tar
     - -rw-rw-r-- 1 student student 8.4M Apr 17 10:15 /tmp/backup.tar.bz2
     - -rw-rw-r-- 1 student student 8.3M Apr 17 10:14 /tmp/backup.tar.gz
     - -rw-rw-r-- 1 student student 8.2M Apr 17 10:15 /tmp/backup.tar.xz
     
4. And then without **-h**.
   - student:/tmp>ls -l /tmp/backup*
     - -rw-rw-r-- 1 student student 8686942 Apr 17 10:14 /tmp/backup2.tar.gz
     - -rw-rw-r-- 1 student student 12226560 Apr 17 10:13 /tmp/backup.tar
     - -rw-rw-r-- 1 student student 8720491 Apr 17 10:15 /tmp/backup.tar.bz2
     - -rw-rw-r-- 1 student student 8686929 Apr 17 10:14 /tmp/backup.tar.gz
     - -rw-rw-r-- 1 student student 8551064 Apr 17 10:15 /tmp/backup.tar.xz
       
5. To obtain more experience, we're going to make backups using the **-j** option to use **bzip** compression,
   and the **-j** option to use **xz** compression.

   - student:/tmp> tar cf /tmp/doc.tar /usr/share/doc
   - student:/tmp> tar xcf /tmp/doc.tar.gz /usr/share/doc
   - student:/tmp> tar jcf /tmp/doc.tar.bz2 /usr/share/doc
   - student:/tmp> tar Jcf /tmp/doc.tar.xz /usr/share/doc
   
   - student:/tmp> ls -lh /tmp/doc.tar* 
      -  -rw-rw-r-- 1 student student 85M Apr 17 10:34 /tmp/doc.tar
      -  -rw-rw-r-- 1 student student 31M Apr 17 10:35 /tmp/doc.tar.bz2
      -  -rw-rw-r-- 1 student student 34M Apr 17 10:34 /tmp/doc.tar.gz
      -  -rw-rw-r-- 1 student student 28M Apr 17 10:36 /tmp/doc.tar.xz

This shows that **xz** performed best, followed by **bz2** and then **gz**. You may have noticed, however, the inverse 
relationship between the compression size reduction an how long it took.
