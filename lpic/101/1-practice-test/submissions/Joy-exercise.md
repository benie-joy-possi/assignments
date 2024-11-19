## Section 1: System Architecture (20 Marks)

1- 
Which of the following commands will display detailed CPU information on a Linux system?
B. lscpu

2- 
What is the difference between BIOS and UEFI in terms of boot process and functionality?
- the UEFI boots faster compared to the BIOS  
- the BIOS uses the MBR while the UEFI uses the ESP
- the BIOS supports less space compared to the UEFI


3- 
- Use a command to determine which kernel modules are loaded in the current system. Explain how to load a new module named dummy.
```sh
lsmod
```
- to load new module named dummy, you enter the /etc/modules configuration file and insert the name of the module. 
in this case "dummy" save the file, exit and source and the module  will be loaded at boot time.

4- 
Explain the purpose of the /proc and /sys directories in Linux.
- The /proc directory is used to stores in fomations about all running processes in your coputer.
- the /sys directory stores device information and kernel data.

## Section 2: Linux Installation and Package Management (20 Marks)
5- 
Which of the following commands installs a package using the APT package manager?

C. apt install package

6- 
Describe the difference between apt and dpkg.
- dpkg is less user friendly compared to apt
- dpkg is a low level package manager, apt is a high level package manager

7- 
Write a command to find and remove orphaned packages in a Debian-based system.
```sh
deborphan | xargs dpkg -r  
```
8- On a Red Hat-based system, explain how to configure a new YUM repository with the base URL http://repo.example.com. Provide a sample .repo file configuration.
-  /etc/yum.repos.d: configuration file
- yum localinstall URL

## Section 3: GNU and Unix Commands (30 Marks)
9- 
Which command is used to display the last 10 lines of a file?

B. tail


10- 
Write a command to count the number of lines containing the word "error" in the file /var/log/syslog.
```sh
grep error /var/log/syslog | wc -l 
```

11- 
Explain the difference between hard links and soft links in Linux. How do you create each?

- a hard link points to the inode of the file 
and if the original file is deleted it doesn't affect the hard link until it is deleted itself 
and also a hard link can only be used within the same filesystem.
```sh
ln hard_link original_file
```
- a soft link points to the file path making it more flexible accrss different filesystems 
but if the original file is deleted the soft link become useless.
```sh
ln -s soft_link original_file
```

12- 
Use the find command to locate all .conf files in /etc that have been modified in the last 7 days.

```sh
sudo find /etc -name '*.conf'  -mtime -7 
```


13- 
Explain the purpose of the cron daemon. Provide an example of a cron job that runs a script named backup.sh every day at midnight.
- the purpose of a cron daemon is to execute scheduled commands or tasks according to a repeated time pattern established during the shedule.

- In the /etc/crontab file you can set the following cron job
```
0 0 * * 0-6 root backup.sh
```

## Section 4: Devices, Filesystems, and FHS (30 Marks)
14- 
What does the command df -h display?

B. Disk usage in human-readable format

15- 
Use a command to display the UUID of all mounted filesystems.
```sh
lsblk -f -o UUID
```

16- 
Explain the difference between ext3 and ext4 filesystems. Mention at least two features of ext4 that make it better.
- EXT3 : max file size 2 TB max filesystem size 16 TB
- EXT4: max file size 16 TB, max filesystem size 1 EB

17- 
You have added a new disk to the system. Write the steps to create a new partition, format it with an ext4 filesystem, and mount it permanently at /data. Include all commands.
- we will call this disk sdx
- list all partition tables of the new disk *fdisk -l /dev/sdx*
- open /dev/sdb *fdisk /dev/sdx*
- use the **n** option to create a new partition
- formart it with an ext4 filesystem *mkfs.ext4 /dev/sdx1*
- mount it in a new directory *mkdir new_directory
- mount /dev/sdx1 /new_directory*

18- 
What is the purpose of the /etc/fstab file? Provide an example entry for mounting a filesystem.
- the /etc/fstab is to store information about all mounted filesystems in computer
- **/dev/nvme0n1p1 /mountpoint ext4 defaults,usrquota,grpquota 0 1**
  
Bonus Question (Optional - 10 Marks)
Explain the boot process in Linux from powering on the machine to a fully loaded OS, detailing the role of GRUB, the kernel, and system initialization.
- After the computer is powered on, the POST is executed to identify hardware failures
- The firmware is initialized (BIOS/ UEFI)
- the motheroard loads the bootloader GRUB
- the GRUB loads the operating system or kernel
- the kernel through the initramfs loads everything else where intervenes system initialization.
  













