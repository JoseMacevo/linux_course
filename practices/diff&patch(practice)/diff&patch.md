# Exercise

### Intro:

Linux and other open source communities often use the **patch utility** to distribute modifications and updates.
Next we're going to give a practical introduction to using **diff and patch**.

It would be a good idea to read the manual pages for both **diff and patch** commands to learn more about advanced
features and techniques, which will help you to work more effectively with **patch**. In particular, the form of patches 
has a lot to do with whether they can be accepted as submitted.

### Exercises:

1. Change to **/tmp** directory.
> cd /tmp/

2. Copy a text file to **/tmp/** directory. For example, copy **/etc/group** to **/tmp**
> cp /etc/group/tmp

3. The **dd** command can't only copy directly from raw disk devices, but also from normal files. Remember, in Linux,
everything is pretty much treated as a file. **dd** can also perform various conversions. For example, the **conv==ucase**,
option will convert all characters to uppercase. We'll use **dd** to copy the text file to a new file in **/tmp** by converting
characters to uppercase, as in: **student:/tmp>**.
> dd if=/tmp/group of=/tmp/GROUP conv==ucase

- 1+1 records in
- 1+1 records out
- 963 bytes (963 B) copied, 0.000456456 s, 2.1 MB/s


4. According to the **patch** manual page, the preferred options for preparing a **patch**, the preferred options for 
preparing a patch with diff are **-Naur** when comparing two directory trees recursively. We're going to ignore the **-a**, 
which means treating all files as text, since **patch** and **diff** should only be used on text files anyway. Since we are
only comparing two files, we don't need to use the **N** or **r** options for **diff**, but we could use them anyway since it
won't make any difference. Compare group and GROUP using **diff** and prepare a suitable patch file.

> student:/tmp> diff -Nur group GROUP > patchfile
> student:/tmp> cat patchfile

```
--- group 2015-04-17 11:03:26.710813740 -0500
      +++ GROUP 2015-04-17 11:15:14.602813740 -0500
      @@ -1,68 +1,68 @@
      -root:x:0:
      -daemon:x:1:
      -bin:x:2:
      -sys:x:3:
      ....
      -libvirtd:x:127:student
      -vboxsf:x:999:
      +ROOT:X:0:
      +DAEMON:X:1:
      +BIN:X:2:
      +SYS:X:3:
      .....

```
5. We can use **patch** to apply patches to the original file, **/tmp/group**, so its contents now match that of the modified
file, **/tmp/GROUP**. We could try the **--dry-run** option first.

> student:/tmp> patch --dry-run group patchfile.
---> checking file group

> student:/tmp> patch group patchfile.
---> patching file group


6. Finally, to show that the original file is now patched and is the same with all characters uppercase, use **diff** on those
two files. The files must be the same and you won't get any diff results.

> student:/tmp> patch group < patchfile.
> student:/tmp> patch < patchfile.
> student:/tmp> diff group GROUP.

studeng:/tmp>


