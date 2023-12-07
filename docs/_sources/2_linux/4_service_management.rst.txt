######################
2.4 Service Management
######################

======================
The Linux Boot Process
======================

Linux requires an initialization system during its boot and startup process.

At the end of the boot process, the Linux kernel loads the **init daemon** (a system and service management mechanism) and passes control over to it and the startup process begins.

During this step, the kernel initializes the first user space process, the init process with process ID 1, and then goes idle unless called again.

Init daemon prepares the user space and brings the Linux host into an operational state by starting all other processes on the system.

Below is a simplified overview of the entire Linux boot and startup process:

    - The system powers up. The BIOS does minimal hardware initialization and hands over control to - the bootloader
    - The bootloader calls the kernel.
    - The kernel loads an initial RAM disk that loads the system drives and then looks for the root file system
    - Once the kernel is set up, it loads the init daemon
    - init daemon takes over and continues to mount the host's file systems and start services

=======
systemd
=======

    - **systemd** (system daemon) is a system and service management mechanism used by modern Linux distributions.
    - it has replaced older service management systems (SysVinit, Upstart)
    - introduced parallel processing of startup scripts
    - improved handling of service dependencies
    - it is backward compatible with SysVinit scripts as described in the Linux Standard Base (LSB) specification
    - systemd is the first process that starts at boot, and it is the last process that terminates at shutdown

=============
systemd Units
=============

systemd introduces the concept of **systemd units** and there are several types, such as a service unit, mount unit, socket unit, and slice unit. Units are defined in unit configuration files, which include information about the unit type and its behavior.

=========  =================================================================================================================================
Unit Type  Description
=========  =================================================================================================================================
Target     A group of units that defines a synchronization point which is used at boot time to start the system in a particular state
Service    A unit of this type starts, stops, restarts or reloads a service daemon such as Apache web server
Socket     A unit of this type activates a service when the service receives incoming traffic on a listening socket
Device     A unit of this type implements device-based activation such as a device driver
Mount      A unit of this type controls the file-system mount point
Automount  A unit of this type provides and controls on-demand mounting of file systems
Swap       A unit of this type encapsulates/activates/deactivates swap partition
Path       A unit of this type monitors files/directories and activates/deactivates a service if the specified file or directory is accessed
Timer      A unit of this type activates/deactivates specified service based on a timer or when the set time is elapsed
Snapshot   A unit that creates and saves the current state of all running units. This state can be used to restore the system later
Slice      A group of units that manages system resources such as CPU, and memory
Scope      A unit that organizes and manages foreign processes
=========  =================================================================================================================================

The following table briefly explains the terms that the systemd uses to describe the status of units.

============== =============================================================================================================================================
Status         Description
============== =============================================================================================================================================
loaded         The unit's configuration file has been successfully read and processed
active exited  Successfully executed the one-time configuration and after execution, the unit is neither running an active process nor waiting for an event
active running Successfully executed the one-time configuration and after execution, the unit is running one or more active processes
active waiting Successfully executed the one-time configuration and after execution, the unit is waiting for an event
inactive dead  Either the one-time configuration failed to execute or not executed yet
============== =============================================================================================================================================

===============
systemd targets
===============

systemd replaces traditional SysVinit **runlevels** with predefined groups of units called **targets**.

Targets are usually defined according to the intended use of the system, and ensure that the required dependencies for that use are met.

The following table shows some standard preconfigured targets, the sysVinit runlevels they resemble, and the use case they address.

========== ======== ======================================================================================
Target     Runlevel Usage
========== ======== ======================================================================================
rescue     1        single-user mode, for recovery of critical system components or configuration
multi-user 2        non-graphical multi-user console access, via local TTYs or network
graphical  5        a GUI sessions. Typically, provides the user with a fully featured desktop environment
custom     4        systemd allows any number of custom-defined targets
========== ======== ======================================================================================

The standard LINUX kernel supports these seven different runlevels :

    * 0 - System halt the system can be safely powered off with no activity.
    * 1 - Single user mode.
    * 2 - Multiple user mode with no NFS(network file system).
    * 3 - Multiple user mode under the command line interface and not under the graphical user interface.
    * 4 - User-definable.
    * 5 - Multiple user mode under GUI (graphical user interface) and this is the standard runlevel for most of the LINUX-based systems.
    * 6 - Reboot which is used to restart the system.

=============
REDHAT FAMILY
=============

.. code-block:: bash

    # List all loaded service units
    systemctl list-units --type=service

    # Check status for NAME service unit
    systemctl status NAME

    # Check if NAME service is enabled
    systemctl is-enabled NAME

    # Check start|stop|restart NAME service
    systemctl start|stop|restart NAME

    # Enable|disable NAME service
    systemctl enable|disable NAME

    # Get default target
    systemctl get-default


.. warning::

    Linux is user-friendly, but it's just very selective about who its friends are.

=========
Questions
=========

1. What is the difference between a service and a daemon?   
    a. A daemon is a program that runs in the background, while a service is a daemon that is started by systemd.
    b. A daemon is a program that runs in the background, while a service is a program that runs in the foreground.
    c. A daemon is a program that runs in the foreground, while a service is a program that runs in the background.
    d. A daemon is a program that runs in the foreground, while a service is a daemon that is started by systemd.

2. Which of the following is not a systemd unit type?
    a. Service
    b. Device
    c. Target
    d. Scope

3. Which of the following is not a systemd target?
    a. rescue
    b. multi-user
    c. graphical
    d. custom

4. Which of the following is not a valid systemd command?
    a. systemctl list-units --type=service
    b. systemctl status NAME
    c. systemctl is-enabled NAME
    d. systemctl update NAME

5. What is the default target in systemd?
    a. rescue
    b. multi-user
    c. graphical
    d. custom

6. How do you check the status of a service?
    a. systemctl status NAME
    b. systemctl list-units --type=service
    c. systemctl is-enabled NAME
    d. systemctl update NAME

7. How do you check if a service is enabled?
    a. systemctl status NAME
    b. systemctl list-units --type=service
    c. systemctl is-enabled NAME
    d. systemctl update NAME

=======
Answers
=======

1. A daemon is a program that runs in the background, while a service is a daemon that is started by systemd.
2. Target
3. custom
4. systemctl update NAME
5. graphical
6. systemctl status NAME
7. systemctl is-enabled NAME