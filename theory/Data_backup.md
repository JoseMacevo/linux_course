# Data_Backup.

There're many ways to do a data backup or even the entire system. Basic ways to do this include using simple
copies with **cp** and using the more robust **rsync**.

Both can be used to synchronize entire directory trees. However, **rsync** is more efficient because it checks if
the file being copied already exists. If the file exists and there's no change in size or modification time,
**rsync** will avoid unnecessary copying and save time. Also, because **rsync** copies only the parts of files that
have changed, it can be very fast.

![](/home/josemacevo/Documents/Development/linux_course/course_images/backup.jpg)

**cp** only can copy files to and from destinations on the local computer (unless you're copying to or from an NFS-mounted
file system), but **rsync** can also be used to copy files from one computer to another. Locations are designated in the
form of someone@host. The someone@ part is optional and is used if the remote user is different from the local user.

**rsync** is very efficient when recursively copying one directory tree to another, because only the differences are transmitted
over the network. We often synchronize the destination directory tree with the source, using the **-r option** to recursively
traverse the directory tree, copying all files and directories below the one listed as the source.

## rsync how to use.


