###################
2.2 File management
###################

====================
Linux directory tree
====================

.. code-block:: bash

	[linux_user@linux_machine ~]$ tree -d -L 2 /

	/                 # root file system
	├── bin           # user executable commands
	├── boot          # kernel, boot configuration files
	├── dev           # (V) device nodes for physical hardware and virtual devices
	├── etc           # system configuration files
	├── home          # user home directories
	├── opt           # additional software
	├── proc          # (V) current state of the running kernel
	├── root          # home directory for the root user
	├── sbin          # system administration commands
	├── sys           # (V) info about hotplug hardware devices
	├── tmp           # temporary files, usually automatically deleted at reboot
	├── usr           # system resources files
	│   ├── lib       # shared libraries used by commands, kernel, programs
	│   ├── lib64     # shared libraries used by commands, kernel, programs
	│   ├── libexec   # binaries run by other programs
	│   ├── local     # custom commands, libraries, programs
	│   ├── share     # man pages, documentation, sample configuration files
	│   └── src       # source code
	└── var           # data that changes frequently
		├── lock      # lock files for devices and other resources shared by multiple applications
		├── log       # system log files
		├── run       # information about the system that is valid until the system is next booted
		├── spool     # cron jobs, mail messages, print jobs
		└── tmp       # temporary files, are not deleted automatically

.. warning::
	
	sudo rm -rf / ; don't try this at ~ 

==============================
File and Directory Permissions
==============================

Linux is a multi-user operating system that allows hundreds of users to log in and work concurrently.

System administrators can grant user access to files and directories, with appropriate rights that allow them to do their job whilst enforcing system security.

------------------
Permission Classes
------------------

	- **User (u)**: The owner of a file/directory
	- **Group (g)**: The members of the file/directory's group
	- **Others (o)**: Any users that are not part of the *user* or *group* classes

----------------
Permission Types
----------------

	- **Read (r/4)**: view/copy file/directory contents
	- **Write (w/2)**: view/copy/move/delete file/directory
	- **Execute (x/1)**: execute file, access directory

------------------
Access Permissions
------------------

=====  ========  =======================
Octal  Symbolic  Description
=====  ========  =======================
0      ---       no permissions
1      --x       execute only
2      -w-       write only
3      -wx       write and execute
4      r--       read only
5      r-x       read and execute
6      rw-       read and write
7      rwx       read, write and execute
=====  ========  =======================

----------------------
Access rights commands
----------------------

.. code-block:: bash

	# The chown (change owner) command alters the user that a file or directory belongs to
	chown --help

	# The chgrp (change group) command alters the group that a file or directory belongs to
	chgrp --help

	# The chmod (change mode) command alters the file permissions
	chmod --help
	
	chmod 700 file

	chmod u=rwx file

-------------------
Special permissions
-------------------

Linux offers three other types of permissions, called **special permission bits** that may be set on executable files or directories to allow them to respond differently for certain operations.

- **setuid** bit: affects only on files, provides non-owners the ability to run executables with the privileges of the owner
- **setgit** bit: has an effect on files and directories, used for group collaboration (alters the standard behavior so that the group of the files created inside the directory, will not be that of the user who created them, but that of the parent directory)
- **sticky** bit: set on directories with effect on its files, all the files in the directory will be modifiable only by their owners. A typical case is the */tmp* directory. Typically, this directory is writable by all users on the system, but a user cannot delete files owned by other users

-------------------
Default permissions
-------------------

Linux assigns default permissions to a file or directory at the time of its creation. Default permissions are calculated based on the **umask** (user mask) value subtracted from a preset value called *initial permissions* (777 for directories, 666 for files).

===================  =========  =====
                     Directory  Files
===================  =========  =====
initial permissions  777 -      666 - 
umask                022        022
default permissions  775        644
===================  =========  =====

------------------
Control attributes
------------------

There are certain **attributes** that may be set on a file or directory in order to control what can or cannot be done to it. For example, you can enable attributes on a file or directory so that no users, including root, can delete, modify, rename, or compress it.

The commands to list or change attributes are **lsattr** and **chattr**.

------------------------------
Inodes, soft links, hard links
------------------------------

Each file within a file system has associated metadata information such as file’s type, size, permissions, owner’s name, owner’s group name, last access/modification time, ACL settings, link count, number of allocated blocks, and pointers to the location in the file system where the file data is actually stored.

That metadata is stored in a 128 byte space on disk which is called **inode** (index node).

The inode is assigned a unique numeric identifier that is used by the kernel for accessing, tracking, and managing the file.

The inode does not store the file’s name in its metadata. The file name and corresponding inode number mapping is maintained in the directory’s metadata.

A **soft link** (a.k.a. a symbolic link or a symlink) associates one file with another (similar to a shortcut in Windows). Each soft link has a unique inode number that stores the path to the file it is linked with.

A **hard link** associates one or more files with a single inode number, making all files indistinguishable from one another. This implies that the files will have identical permissions, ownership, time stamp, and file contents. Changes made to any of the files will be reflected in the other linked files as well.

---------------
Useful commands
---------------

.. code-block:: bash

	# Shows information about file system disk usage
	df -h

	# Shows information about directory and file sizes on the disk
	du -h /var

	# Shows information about directory and file sizes on the disk
	# Only on the first level of directories
	# Sort output in reversed order and human-readable format
	du -h --max-depth=1 /usr | sort -rh

	# Find and print all directories in /usr
	find /usr -type d

	# Find and print all files with .log extension in /var/log
	find /var/log -type f -name "*.log"

	# Find directories and files owned by Alice
	find / -user alice

	# Find directories and files owned by the billing group
	find / -group billing

	# Find files larger than 10MB and list them in long format
	find / -type f -size +10M -exec ls -lh {} \;

====
TODO
====

1. create **/opt/billing** directory
2. create **/opt/billing/clients** and **/opt/billing/invoices** files
3. configure **alice** user as owner for **/opt/billing** directory and its contents
4. configure **billing** group as owner for **/opt/billing** directory and its contents
5. configure access rights for **/opt/billing** directory:
	a. read, write and execute for **alice** user
	b. read and execute for **billing** group
	c. read and execute for everyone else
6. remove access rights to others for all files in the **/opt/billing** directory
7. add write permissions on **/opt/billing/invoices** for **billing** group
8. make **john** as owner for **/opt/billing/clients** and assign him read-only rights
9. make **alice** as owner for **/opt/billing/invoices** and assign her read-only rights

.. warning::

	To err is human ... to really f*ck up requires the root password.

================
Solution to TODO
================

1. mkdir /opt/billing
2. touch /opt/billing/clients /opt/billing/invoices
3. chown alice /opt/billing
4. chgrp billing /opt/billing
5. chmod 755 /opt/billing
6. chmod o-r /opt/billing/*
7. chmod g+w /opt/billing/invoices
8. chown john /opt/billing/clients
   chmod u-w /opt/billing/clients
9. chown alice /opt/billing/invoices
   chmod u-w /opt/billing/invoices