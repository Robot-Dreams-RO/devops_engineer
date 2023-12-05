##################
2.6 System logging
##################

.. note::

    Log files are files that contain messages about the system, including the kernel, services, and applications running on it.

There are different log files for different information. For example, there is a default system log file, a log file just for security messages, and a log file for cron tasks. Everything from kernel events to user actions can be logged, allowing you to see almost any action performed on your servers.

Log files can be very useful when trying to troubleshoot a problem with the system such as trying to start a service or when looking for unauthorized login attempts to the system.

In RHEL log files are controlled by a daemon called ``rsyslogd``.

=================
Linux System Logs
=================

Linux has a special directory for storing logs called ``/var/log``.

This directory contains logs from the OS itself, services, and various applications running on the system.

Some of the most important Linux system logs include

    #. ``/var/log/messages`` stores all global system activity data, including startup messages
    #. ``/var/log/secure`` stores all security-related events such as logins, root user actions, and output from pluggable authentication modules (PAM)
    #. ``/var/log/cron`` stores information about scheduled tasks (cron jobs)
    #. ``/var/log/maillog`` contains information about emails relayed by the local mail server

=================
Log file rotation
=================

With the amount of logging that is possible, you need to be able to control the size of log files.

This is done using the ``logrotate`` command, which is usually run as a cron job.

The general idea behind the ``logrotate`` command is that log files are periodically backed up, and a new log is started.

Several generations of logs are kept, and when a log ages to the last generation, it may be archived/deleted.

==========
Journalctl
==========

Logs are usually dispersed throughout the system, handled by different daemons and processes, and can be fairly difficult to interpret when they span multiple applications.

Systemd attempts to address these issues by providing a centralized management solution for logging all kernel and userland processes. The system that collects and manages these logs is known as the **journal**.

===========
Cheat sheet
===========

.. code-block:: bash

    # print last 100 lines
    tail -n 100 /var/log/messages

    # follow log
    tail -f /var/log/secure

    # every journal entry that is in the system will be displayed
    journalctl

    # journal entries collected since the most recent reboot
    journalctl -b

    # display only kernel messages
    journalctl -k

    # display the last 20 messages
    journalctl -n 20

    # actively follow the logs as they are being written
    journalctl -f

    # filter messages by priority
    journalctl -p err

    # filter messages by the service unit
    journalctl -u sshd

    journalctl -u crond --since today

    # show listing of last logged-in users
    last                  

    # show a listing of users logged in since the last boot
    lastb

.. warning::

    The only problem with troubleshooting is that sometimes trouble shoots back.

=========
Questions
=========

1. What is the name of the daemon that controls log files in RHEL?

   a. ``rsyslogd``
   b. ``syslogd``
   c. ``logd``
   d. ``logrotate``

2. Which of the following log files contains information about emails relayed by the local mail server?

   a. ``/var/log/messages``
   b. ``/var/log/secure``
   c. ``/var/log/cron``
   d. ``/var/log/maillog``

3. Which of the following commands can be used to display the last 20 messages from the journal?

   a. ``journalctl -n 20``
   b. ``journalctl -f``
   c. ``journalctl -p err``
   d. ``journalctl -u sshd``

4. Which of the following commands can be used to display the last 20 lines of the ``/var/log/messages`` file?

   a. ``tail -n 20 /var/log/messages``
   b. ``tail -f /var/log/messages``
   c. ``tail -n 20 /var/log/messages``
   d. ``tail -n 20 /var/log/messages``

=======
Answers
=======

1. a
2. d
3. a
4. c
