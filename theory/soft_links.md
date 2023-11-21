### Soft links or symlinks (symbolics).

The soft_links **-soft** (or simbolics) are created using the **-s** option.

- **ln -s file1 file3** -> creacion del softlink
- **ls -li file1 file3** -> test del softlink


The symbolic links don't take additional space on de system, they're very useful as they can be easily modified to point to different places.
An easy way to create shortcuts from */home*.

They can point to objects even in different file systems, partitions and/or disks and other media, which may or may not exist, in the latter case a **dangling link** would be obtained. 
