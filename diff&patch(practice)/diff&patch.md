# Exercise

### Intro:

Linux and other open source communities often use the **patch utility** to distribute modifications and updates.
Next we're going to give a practical introduction to using **diff and patch**.

It would be a good idea to read the manual pages for both **diff and patch** commands to learn more about advanced
features and techniques, which will help you to work more effectively with **patch**. In particular, the form of patches 
has a lot to do with whether they can be accepted as submitted.

1. Change to **/tmp** directory.
> cd /tmp/

2. Copy a text file to **/tmp/** directory. For example, copy **/etc/group** to **/tmp**
> cp /etc/group/tmp

3. The **dd** command can't only copy directly from raw disk devices, but also from normal files. Remember, in Linux,
everything is pretty much treated as a file. **dd** can also perform various conversions. For example, the **conv==ucase**,
option will convert all characters to uppercase. We'll use **dd** to copy the text file to a new file in **/tmp** by converting
characters to uppercase, as in: **student:/tmp>**.
>dd if=/tmp/group of=/tmp/GROUP conv==ucase

- 1+1 records in
- 1+1 records out
- 963 bytes (963 B) copied, 0.000456456 s, 2.1 MB/s



