#####################
2.3 Managing Software
#####################

.. note::

    **RHEL** is essentially a set of RPM packages grouped to form an operating system. It is built around the Linux kernel and includes thousands of packages that are digitally signed, tested, and certified.

A software package is a group of files organized in a directory structure and metadata that makes up a software application. Files contained in a package include installable scripts, configuration files, library files, commands, and related documentation.

All metadata related to packages is stored at a central location and includes information such as package versioning, the location it is installed at, checksum values, and a list of included files with their attributes.

Usually, software packages follow a standard naming convention.

.. note::

    name.version.release.architecture

===========================
Useful dnf and rpm commands
===========================

.. code-block:: bash
    
    # Search package details for the given string
    dnf search KEYWORD
    
    # Display details about a package or group of packages
    dnf info KEYWORD

    # Find what package provides the given value
    dnf provides */KEYWORD

    # List files in the package
    rpm -ql package_name

    # Find the package that owns the file
    rpm -qf file_name

====
TODO
====

1. dnf: find packages containing a file named ``httpd``
2. dnf: install Apache HTTP Server
3. rpm: find which package owns the ``/etc/fedora-release`` file (to get the info start with ``rpm --help`` | grep what)
4. rpm: find what other files were installed by the above packet

.. warning::
    
    Installing new software
    
    There are lots of different ways to install software on Linux systems. Installing directly from your distros official software repositories is the safest option, but sometimes the application or version you want simply isn't available that way. When installing via any other mechanism, make sure you're getting the files from an official source for the project in question. |

.. warning::

    Planning is for those who don't know how to troubleshoot.

=================
Solution to TODOs
=================

1. ``dnf provides */httpd``
2. ``dnf install httpd``
3. ``rpm -qf /etc/fedora-release``
4. ``rpm -ql httpd-2.4.37-10.fc29.x86_64``