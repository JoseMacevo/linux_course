# <span style="color:blue"> Data_Backup.</span>

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

## <span style="color:red"> rsync how to use.</span>

**rsync** is a powerful utility. For example, a very useful way to backup a project directory could be to use the following command.

> rsync -r project-X archive-machine:archives/project-X

**Note** that **rsync** can be very destructive. Accidental misuse can cause extensive damage to data and programs by inadvertently
copying changes to places where they aren't wanted. Be careful to specify the correct options and routes well. It's strongly
recommended that you first test **rsync** using the **-dry-run** command (running in tests without making any actual changes) to
ensure that it provides the results that you want.

![](/home/josemacevo/Documents/Development/linux_course/course_images/keycap.jpg)

To use **rsync** at the command prompt, type **rsync <source_file><target_file>** where any of the files can be on the
local computer or on a network computer. The contents of **source_file** will be copied to **destination_file**.

A good combination of options is shown in:

> rsync --progress -avrxH --delete <source_file><target_file>


