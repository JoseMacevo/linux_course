# Main linux directories.

## User home directories overview.

In this section, we will learn to indentify and differentiate the most important linux directories.

Each user has a personal dirctory normaly located in **/home**

On modern linux systems the **/root** is nothing more than the root user's home directory (or superuser or system administrator account).

On multiuser systems, the directories infraestructure **/home** usually is mounted like a independent system files on its own partition
or even exported (shared) remotely via NFS network.

Sometimes you can group users depending on their department or function and create subdirectories in the **/home** directory for Each
of these groups.

Example:

- /home/faculty/
- /home/staff/
- /home/students/


## /bin /sbin directories.

The **/bin** directory has executables binaries, essential commands used to boot the system or use it in single-user mode,
and essential commands required by all users of the system, such as **cat**, **cp**, **ls**, **mv**, **ps** and **rm**.

**/bin directory**
![/bin directory](/home/josemacevo/Documents/Development/linux_course/course_images/lsbin.png)

The same way the **/sbin** directory is designed for essential binaries related to system administration, such as 
**fsck** and **ip**. To see a list of these programs we only need type:


- *$ ls /bin /sbin/*


**/sbin directory**
![/sbin directory](/home/josemacevo/Documents/Development/linux_course/course_images/lssbin.png)



Commands that aren't essential (theorically) for the system boot or operate in single_user mode are placed in the
**/usr/bin** and **usr/sbin** directories. Historically, this was done so that **/usr** could be mounted as a standalone filesystem
that could be mounted at a later stage of sytem startup or even over a network. However, todya most consider this distinction to be
obsolete. In fact, it has been discovered that many distributions cannot boot with this separation, as this modality hasn't been used
or tested for a long time.
j
Thus, in some of the newer Linux distros **/usr/bin** and **bin** are symbolically linked to each other, as are **/usr/sbin** and **/sbin**.

## /proc file system.

  Some file systems, like the mounted in **/proc**, are called **pseudo file systems** because they dont have a permanent presence anywhere
on the disk.

The **/proc** file system has virtual files (files that only exists in the memory) that allow to us to see the kernel data which are 
constantly changing. **/proc** has directories and files that imitate the kernel instructions and the configuration info. It dosen't has
real files, only information about the system at runtime per example memory system, mounted devices, hardware configuration, etc... Some 
important entries are:

- **proc/cpuinfo**
- **proc/interrupts**
- **proc/meminfo**
- **proc/mounts**
- **proc/partitions**
- **proc/version**

**/proc** also has subdirectories, included:

- **proc/<Process-ID-#>**
- **proc/sys**


The next example shows that there's a directory for each process running on the system, which contains vital information about it.
The second example shows a virtual directory that contains a lot of information about the entire system, in particular its hardware and
configuration. The **/proc file system** is very usefull because the information it reports is collected only as needed and never
requires disk storage.

![example](/home/josemacevo/Documents/Development/linux_course/course_images/1.png)


## /dev directory.

The **/dev** directory contains **the device nodes**, a pseudofile type used by the most hardware and software devices, except the network devices
This directory:
- It's empty when the partition disc isn't mounted.

- Contains entries created by the **udev**system, which creates and manages all device nodes in linux, dinamically creating them when the devices
are found. The **/dev** contains elements such as:

    1. /dev/sda1(first hard disc partition).
    2. /dev/lp1(second printer).
    3. /dev/random(random numbers source).

**/dev directory**

![lsdev](/home/josemacevo/Documents/Development/linux_course/course_images/lsdev.png)


## /var directory.

The **/var** directory contains files that are expected to change its size and content as the system runs(var means variable), such as entries in
the following directories.

- System log files: /var/log
- Database files and packages: /var/lib.
- Print queues: /var/spool.
- Temporary files: /var/tmp.

**The /var directory**
![/var](/home/josemacevo/Documents/Development/linux_course/course_images/lsvar.png)

The **/var** directory can be placed on its own file system so that file growth can be accommodated and any files that suddenly grow very large
won't fatally affect the system. Network services such as /var/ftp(ftp service) and /var/www (the HTTP web service) are also located in /var.

![/var](/home/josemacevo/Documents/Development/linux_course/course_images/vardir.es.png)


## /etc directory.

The **/etc** directory is where the system configuration files are. It doesn't executable binaries, although there are some executable scripts.
For example, **/etc/resolv.conf** tells to the system where to go on the network to obtain the host name in the IP addresses (DNS) mappings.
Files such as **passwd**, **shadow** and groups for managing user accounts are located in the **/etc** directory. While some distros have Historically
had their own extensive infraestructure unde **/etc** (for example, Red Hat and SUSE, have used **/etc/sysconfig**), with the advent of systemd there's
much more uniformity between distros today.

Note that **/etc** is for system-wide configuration files and only the superuser can modify the files there. User-especific configuration files are
always located in your **/home** directory.

![/etc](/home/josemacevo/Documents/Development/linux_course/course_images/debianetc.png)


## /boot directory.

The **/boot** directory contains the few essential files required to boot the system. For each alternative kernel installed on the system there're four files.

1. **vmlinuz** the compressed kernel, required to boot.
2. **initramfs** the initial ram file system, required for booting, sometimes called **initrd**, rather than **initramfs.**
3. **config** The kernel configuration file, which is only used for debugging and control.
4. **system.map** kernel symbol table, only used for debugging.

Each one of this files has a kernel version attached to its name.

The **Grand Unified Bootloader (GRUB)** files such as **/boot/grub/grub.conf** or **/bot/grub2/grub2.cfg** are also located in the **/boot** directory.

The next image shows an example listing of the **/boot** directory, taken from a RHEL system that has multiple kernels installed, including
the distro-supplied and custom-built kernels. The names will vary and things will be a little different in a different distro.

![/boot](/home/josemacevo/Documents/Development/linux_course/course_images/boot.png)


## The /lib and /lib64.

**/lib** contains libraries (common code shared by apps and required for them to run) for the essential **/bin** and **/sbin** programs. These library
file name begin with **id** or **lib** for example, **/lib/libncurses.so.5.9**.

Most of them are what are known as dynamically loaded libraries (also known as shared libraries or shared objects (Shared Objects SO)). On some linux 
distros there's a **/lib64** directory that contains 64-bit libraries, while **/lib** contains 32-bit versions.

