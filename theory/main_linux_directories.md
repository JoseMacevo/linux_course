# <span style="color:blue">Main Linux directories.</span>

## <span style="color:red">User home directories overview.</span>

In this section, we will learn to identify and differentiate the most important linux directories.

Each user has a personal directory normally located in **/home**

On modern linux systems the **/root** is nothing more than the root user's home directory (or superuser or system administrator account).

On multiuser systems, the directories infraestructure **/home** usually is mounted like a independent system files on its own partition
or even exported (shared) remotely via NFS network.

Sometimes you can group users depending on their department or function and create subdirectories in the **/home** directory for Each
of these groups.

Example:

- /home/faculty/
- /home/staff/
- /home/students/


## <span style="color:red"> /bin /sbin directories. </span>

The **/bin** directory has executables binaries, essential commands used to boot the system or use it in single-user mode,
and essential commands required by all users of the system, such as **cat**, **cp**, **ls**, **mv**, **ps** and **rm**.

**/bin directory**
![](/home/josemacevo/Documents/Development/linux_course/course_images/lsbin.png)

The same way the **/sbin** directory is designed for essential binaries related to system administration, such as 
**fsck** and **ip**. To see a list of these programs we only need type:


> *$ ls /bin /sbin/*


**/sbin directory**
![](/home/josemacevo/Documents/Development/linux_course/course_images/lssbin.png)



Commands that aren't essential (theorically) for the system boot or operate in single_user mode are placed in the
**/usr/bin** and **usr/sbin** directories. Historically, this was done so that **/usr** could be mounted as a standalone filesystem
that could be mounted at a later stage of sytem startup or even over a network. However, todya most consider this distinction to be
obsolete. In fact, it has been discovered that many distributions cannot boot with this separation, as this modality hasn't been used
or tested for a long time.

Thus, in some of the newer Linux distros **/usr/bin** and **bin** are symbolically linked to each other, as are **/usr/sbin** and **/sbin**.

## <span style="color:red"> /proc file system. </span>

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

![](/home/josemacevo/Documents/Development/linux_course/course_images/1.png)


## <span style="color:red"> /dev directory.</span>

The **/dev** directory contains **the device nodes**, a pseudofile type used by the most hardware and software devices, except the network devices
This directory:
- It's empty when the partition disc isn't mounted.

- Contains entries created by the **udev**system, which creates and manages all device nodes in linux, dinamically creating them when the devices
are found. The **/dev** contains elements such as:

1. /dev/sda1(first hard disc partition).
2. /dev/lp1(second printer).
3. /dev/random(random numbers source).

**/dev directory**

![](/home/josemacevo/Documents/Development/linux_course/course_images/lsdev.png)


## <span style="color:red">/var directory.</span>

The **/var** directory contains files that are expected to change its size and content as the system runs(var means variable), such as entries in
the following directories.

- System log files: /var/log
- Database files and packages: /var/lib.
- Print queues: /var/spool.
- Temporary files: /var/tmp.

**The /var directory**
![](/home/josemacevo/Documents/Development/linux_course/course_images/lsvar.png)

The **/var** directory can be placed on its own file system so that file growth can be accommodated and any files that suddenly grow very large
won't fatally affect the system. Network services such as /var/ftp(ftp service) and /var/www (the HTTP web service) are also located in /var.

![](/home/josemacevo/Documents/Development/linux_course/course_images/vardir.es.png)


## <span style="color:red">/etc directory.</span>

The **/etc** directory is where the system configuration files are. It doesn't executable binaries, although there are some executable scripts.
For example, **/etc/resolv.conf** tells to the system where to go on the network to obtain the host name in the IP addresses (DNS) mappings.
Files such as **passwd**, **shadow** and groups for managing user accounts are located in the **/etc** directory. While some distros have Historically
had their own extensive infraestructure unde **/etc** (for example, Red Hat and SUSE, have used **/etc/sysconfig**), with the advent of systemd there's
much more uniformity between distros today.

Note that **/etc** is for system-wide configuration files and only the superuser can modify the files there. User-especific configuration files are
always located in your **/home** directory.

![](/home/josemacevo/Documents/Development/linux_course/course_images/debianetc.png)


## <span style="color:red">/boot directory.</span>

The **/boot** directory contains the few essential files required to boot the system. For each alternative kernel installed on the system there're four files.

1. **vmlinuz** the compressed kernel, required to boot.
2. **initramfs** the initial ram file system, required for booting, sometimes called **initrd**, rather than **initramfs.**
3. **config** The kernel configuration file, which is only used for debugging and control.
4. **system.map** kernel symbol table, only used for debugging.

Each one of this files has a kernel version attached to its name.

The **Grand Unified Bootloader (GRUB)** files such as **/boot/grub/grub.conf** or **/bot/grub2/grub2.cfg** are also located in the **/boot** directory.

The next image shows an example listing of the **/boot** directory, taken from a RHEL system that has multiple kernels installed, including
the distro-supplied and custom-built kernels. The names will vary and things will be a little different in a different distro.

![](/home/josemacevo/Documents/Development/linux_course/course_images/boot.png)


## <span style="color:red">The /lib and /lib64.</span>

**/lib** contains libraries (common code shared by apps and required for them to run) for the essential **/bin** and **/sbin** programs. These library
file name begin with **id** or **lib** for example, **/lib/libncurses.so.5.9**.

Most of them are what are known as dynamically loaded libraries (also known as shared libraries or shared objects (Shared Objects SO)). On some linux 
distros there's a **/lib64** directory that contains 64-bit libraries, while **/lib** contains 32-bit versions.

In recent Linux distros we can find:

![](/home/josemacevo/Documents/Development/linux_course/course_images/lsFlib.png)

> */lib and /lib64 directories.*


That's, just as for **/bin** and **/sbin**, the directories only point to those under **/usr**.
The kernel modules(kernel code, often device drivers, which can be loaded and unloaded without rebooting the system) are located in **/lib/modules/<kernel-version-number>**.

![](/home/josemacevo/Documents/Development/linux_course/course_images/libmodules.png)

> */lib/modules content*


## <span style="color:red"> Removable media: the /media, /run and /mnt directories.</span>

Removable media such as USB drivers, CD's and DVD's are often used. In order for the material to be accesible through the normal file system, they must be mounted in
a convenient location. Most linux systems are configured so that any removable media is auromatically mounted when the system detects that something has been plugged in.

While historically this was done under the **/media** directory, modern linux distros place these mount points under the /run directory. For example, a USB pen drive
labeled myusbdrive for a username student would be mounted in **/run/media/student/myusbdrive**.

![](/home/josemacevo/Documents/Development/linux_course/course_images/Forty_years_of_Removable_Storage.jpg)

The **/mnt** directory has been used since the early days of UNIX to temporarily mount file systems. These can be found on removable media, but can also very often be
network files systems, which are tipically unmounted, or they can be temporary partitions, or so-called loopback file systems, which are files that appear to be partitions.

![](/home/josemacevo/Documents/Development/linux_course/course_images/run.png)

> */run directory*

## <span style="color:red">Additional directories:</span>

There are a few additional directories found in the root directory **(/):** 

|Directory_name|                        Used to                                                                                                                              |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
|**/opt**      |Optional application software packages.                                                                                                                      |
|              |                                                                                                                                                             |
|**/sys**      |Pseudo virtual file system that provides information about the system and its hardware, can be used to modify system parameters and for debugging purposes.  |
|              |                                                                                                                                                             |
|**/srv**      |Site-specific data provided by the system, rarely used.                                                                                                      |
|              |                                                                                                                                                             |
|**/temp**     |Temporary file, in some distros they're erased after a reboot and/or may be a ramdisk in memory.                                                             |
|              |                                                                                                                                                             |
|**/usr**      |Multi-user apps, utilities and data.                                                                                                                         |
 


## <span style="color:red">/usr directory tree.</span>

The **/usr** directory theorically contains non-essential programs and scripts (in the sense that they shouldn't be necessary to initially boot the system) and has at
least the following directories.


|Directory_name    |                        Used to                                                                             |
|------------------|------------------------------------------------------------------------------------------------------------|
|**/usr/include**  | Header files used to compile applications.                                                                 |
|                  |                                                                                                            | 
|**/usr/lib**      | Libraries for programs in **/usr/bin and /usr/sbin**                                                       |
|                  |                                                                                                            | 
|**/usr/lib64**    | 64 bit libraries for 64 bit programs in **/usr/bin** and **/usr/sbin**.                                    |
|                  |                                                                                                            |
|**usr/sbin**      | Non essential system binaries, suchs as system daemons.                                                    |
|                  |                                                                                                            | 
|**/usr/share**    | Shared data used by apps, generally architecture-independent.                                              |
|                  |                                                                                                            |
|**/usr/src**      | Source code, typially for the Linux kernel.                                                                | 
|                  |                                                                                                            |
|**/usr/local**    | Local computer specific data and programs, subdirectories include **bin, sbin, lib, share, include, etc.** |
|                  |                                                                                                            |
|**/usr/bin**      | This is the main directory of system executable commands.                                                  |


