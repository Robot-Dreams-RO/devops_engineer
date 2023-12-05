######################
2.7 Linux File Systems
######################

# Data storage types
====================

#. **Block Level**
    #. offered directly to the Operating System as raw devices
    #. controlled by the OS, which can create partitions and file systems on them
    #. cannot be shared across servers
    #. types of block-level storage solutions: **DAS** (Direct Attached Storage), **SAN** (Storage Area Network) systems
    #. **DAS** (Direct Attached Storage):
        #. a DAS is anything that is directly attached to a server or computer
        #. a DAS device could be a single internal hard disk or multiple external hard disks (JBOD)
        #. there are no networking layers between the computer and the storage
        #. protocols: SATA, SCSI, SAS
        #. for redundancy and/or performance disks can be clustered in **RAID**

    #. **SAN** (Storage Area Network):
        #. an enterprise system that provides access to consolidated block\-level data storage
        #. devices exposed by SANs appear to the operating system as locally\-attached devices
        #. comprised of dedicated hardware managed by a specialized software
        #. protocols: **FCP** (SCSI over Fiber Channel), **iSCSI** (SCSI over TCP/IP), **FCoE**
#. **File Level**
    #. data is stored as files and presented to OSes as a hierarchical directories structure
    #. file access management features, such as ownership and permissions
    #. can be shared across servers
    #. protocols: **NFS**, SMB/CIFS
    #. devices that offer file-level access are called **NAS** (Network Attached Systems)
#. **Object Level**
    #. an approach to address and manipulate data storage as discrete units, called objects
    #. keeps the blocks of data that make up a file together and adds all of its associated metadata to that file
    #. also adds extended metadata to the file and eliminates the hierarchical structure used in file storage, placing everything into a flat address space, called a storage pool
    #. it is generally slower than a file or block storage system, but it is highly scalable
    #. Amazon Simple Storage Service (Amazon S3), OpenStack Swift, Ceph

=================
Disks, partitions
=================

#. **disks** are just raw physical/virtual means to store data, what lacks is an organization
#. that organization comes in the name of **partition**
#. a **partition** is a logical form of boundary, it is used to divide the disk into logical units
#. partitions store data, but where are partitions stored?
#. partitions are stored in what's called a **partition table**
#. partition tables store the data associated with partitions, where a partition starts, where a partition, etc
#. however partitions are not enough to store data in an ordered manner
#. to do that we need a **file system**
#. a file system takes care of storing pieces of data - **files**
#. files themselves are just a bunch of data that are stored through the file system, which resides in a partition, which is recorded in a partition table, all of this, inside a disk

======================
Logical Volume Manager
======================

#. **LVM** is a storage abstraction layer that allows for very flexible management of block-level devices
#. provides features like the ability to add disk space to a logical volume and its filesystem while that filesystem is mounted and active
#. allows for the collection of multiple physical hard drives and partitions into a single volume group which can then be divided into logical volumes.
#. terminology:
    #. **physical volumes**: physical disks, or disk partitions
    #. **volume groups**: seen as a *"virtual partition"* which comprises an arbitrary number of physical volumes
    #. **logical volumes**: contained in the volume groups they can be bigger than any single physical volume you might have. These will be formatted with a file system

============
File systems
============

#. a **file system** is a structured representation of data and a set of metadata describing this data
#. it is applied to the storage during the **format** operation
#. common file system types: ext3, **ext4**, **xfs**, fat, ntfs; nfs, smbfs/cifs

=========
Questions
=========

1. What is the difference between block-level and a file-level storage?

   a. Block-level storage is offered directly to the Operating System as raw devices, while file-level storage is stored as files and presented to OSes as a hierarchical directories structure.
   b. Block-level storage is stored as files and presented to OSes as a hierarchical directories structure, while file-level storage is offered directly to the Operating System as raw devices.
   c. Block-level storage is stored as files and presented to OSes as a hierarchical directories structure, while file-level storage is offered directly to the Operating System as raw devices.
   d. Block-level storage is offered directly to the Operating System as raw devices, while file-level storage is stored as files and presented to OSes as a hierarchical directories structure.

2. What is the difference between a disk and a partition?

    a. A disk is a logical form of boundary, it is used to divide the disk into logical units, while a partition is just raw physical/virtual means to store data.
    b. A disk is just raw physical/virtual means to store data, while a partition is a logical form of boundary, it is used to divide the disk into logical units.
    c. A disk is a logical form of boundary, it is used to divide the disk into logical units, while a partition is a logical form of boundary, it is used to divide the disk into logical units.
    d. A disk is just raw physical/virtual means to store data, while a partition is just raw physical/virtual means to store data.

3. What is the difference between a partition and a partition table?

    a. A partition is a logical form of boundary, it is used to divide the disk into logical units, while a partition table is just raw physical/virtual means to store data.
    b. A partition is just raw physical/virtual means to store data, while a partition table is a logical form of boundary, it is used to divide the disk into logical units.
    c. A partition is a logical form of boundary, it is used to divide the disk into logical units, while a partition table is a logical form of boundary, it is used to divide the disk into logical units.
    d. A partition is just raw physical/virtual means to store data, while a partition table is just raw physical/virtual means to store data.

4. What is the difference between a partition table and a file system?

    a. A partition table is a logical form of boundary, it is used to divide the disk into logical units, while a file system is just raw physical/virtual means to store data.
    b. A partition table is just raw physical/virtual means to store data, while a file system is a logical form of boundary, it is used to divide the disk into logical units.
    c. A partition table is a logical form of boundary, it is used to divide the disk into logical units, while a file system is a logical form of boundary, it is used to divide the disk into logical units.
    d. A partition table is just raw physical/virtual means to store data, while a file system is just raw physical/virtual means to store data.

5. What is the difference between a file system and a file?

    a. A file system is a structured representation of data and a set of metadata describing this data, while a file is a logical form of boundary, it is used to divide the disk into logical units.
    b. A file system is a logical form of boundary, it is used to divide the disk into logical units, while a file is a structured representation of data and a set of metadata describing this data.
    c. A file system is a structured representation of data and a set of metadata describing this data, while a file is a structured representation of data and a set of metadata describing this data.
    d. A file system is a logical form of boundary, it is used to divide the disk into logical units, while a file is a logical form of boundary, it is used to divide the disk into logical units.

=======
Answers
=======

1. a
2. b
3. c
4. c
5. b