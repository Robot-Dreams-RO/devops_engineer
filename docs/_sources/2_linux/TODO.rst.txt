====
TODO
====

1. What does this command ``find / -size +10M -exec ls -l {} \;`` do?

    a. It finds all files using ``ls -l`` and hands them off to the find command to display.
    b. It finds all files older than 10 minutes and long lists them using the ``ls`` command.
    c. It finds all files larger than 10 MB and long lists them using the ``ls`` command.
    d. It uses the ``ls`` command to find all files in the filesystem matching the {} wildcard.

2. Which command will tell you how long a system has been running?

    a. log
    b. uptime
    c. runtime
    d. access

3. Which command in Bash executes the last line in the shell history that starts with ``ls``?

    a. !
    b. !!
    c. !*
    d. !ls

4. Why doesn't ``passwd -l`` keep a user from logging in via other methods?

    a. The passwd command is not used for locking passwords.
    b. There is no password ``-l`` option.
    c. It locks only the password, not the account, so users can still authenticate with keys or other methods.
    d. It does lock the account, keeping users from logging in even if they are using other authentication methods.

5. Why might you use the usermod command?

    a. to log out a user
    b. to lock a user's account
    c. to change global user account settings
    d. to set a user's password

6. With most GNU commands, if an option is a word, not a letter, what will it be preceded by?

    a. two dashes --
    b. a backslash \
    c. a slash /
    d. one dash -
    e. nothing

7. Which command do you use to rename a file in Linux?

    a. mv
    b. rn
    c. rename
    d. ren

8. What is the command to change the owner of a file?
    
    a. chown
    b. chowner
    c. chownfile
    d. chownf

9. What is the command to get a list of all the users on a system?

    a. users
    b. who
    c. whoami
    d. w

10. What is the command to check if a port is used?

    a. port
    b. portcheck
    c. lsof
    d. netstat

11. How can we see how much disk is used?

    a. df
    b. du
    c. ls
    d. cd

12. How can we see how much memory is used?
    
    a. df
    b. du
    c. ls
    d. free

13. How can we see how much CPU is used?
        
    a. df
    b. du
    c. ls
    d. top

14. How can we see how much network is used?

    a. df
    b. du
    c. ls
    d. netstat

15. How can remove a service from the system?

    a. systemctl stop
    b. systemctl disable
    c. systemctl remove
    d. systemctl delete

16. How can I check if a service is running?

    a. systemctl status
    b. systemctl check
    c. systemctl test
    d. systemctl run

.. note::
    
    Some things Man was never meant to know. For everything else, there's Google.

==================
Solutions to TODOs
==================

1. **Answer:** c. It finds all files larger than 10 MB and long lists them using the ``ls`` command

**Explanation:** 

    The ``find`` command is used to search for files and directories in a specified location. In this case, the search is being performed on the root directory ``/``. The ``-size`` option is used to specify the size of the files to search for. The ``+`` sign indicates that the search should be for files larger than the specified size, which in this case is 10 megabytes. The ``M`` indicates that the size is in megabytes.
    The ``-exec`` option is used to execute a command on each file that is found. In this case, the ``ls -l`` command is executed on each file. The ``ls`` command is used to list the files in a directory, and the ``-l`` option is used to display the file details in a long format. The ``{}`` is a placeholder for the file name that is found by the find command. The ``\;`` is used to indicate the end of the command.
    Overall, this command is useful for finding large files on a system that may be taking up too much space.

2. **Answer:** b. uptime

**Explanation:** 

    The ``uptime`` command is used to display how long a system has been running. It also displays the number of users currently logged in and the system load averages for the past 1, 5, and 15 minutes. The commands ``log``, ``runtime``, ``access`` are not valid.

3. **Answer:** b. !ls

**Explanation:**

    a. ! - This is used to reference events in the command history. You use it with a number or a string to reference specific commands. For instance, !5 would re-execute the fifth command in the history.
    b. !! - This is a shortcut to repeat the last command. It's equivalent to executing the very last command you ran.
    c. !* - This references all the arguments of the previous command. For example, if you typed echo hello world, then typing cat !* would be equivalent to typing cat hello world.
    d. !ls - In Bash, the command !ls will execute the last command in the shell history that starts with "ls".

4. **Answer:** c. It locks only the password, not the account, so users can still authenticate with keys or other methods.

**Explanation:**

    The ``passwd`` command is used to change a user's password. It locks only the password, not the account, so users can still authenticate with keys or other methods. 

5. **Answer:** d. to set a user's password

**Explanation:**

    The ``usermod`` command is used to modify a user account. It can be used to change the user's home directory, shell, and group. It can also be used to set a user's password.

6. **Answer:**  a. two dashes ``--``

**Explanation:**

    With most GNU commands, if an option is a word, not a letter, it will be preceded by two dashes ``--``. For example, the ``--help`` or ``-h`` option is used to display the help information for a command. 

7. **Answer:**  a. mv

**Explanation:**

    The ``mv`` command is used to move or rename files and directories. For example, ``mv file1 file2`` would rename file1 to file2. The ``rn``, ``rename``, and ``ren`` commands are not valid.

8. **Answer:**  a. chown

**Explanation:**

    The ``chown`` command is used to change the owner of a file or directory. For example, ``chown user1 file1`` would change the owner of file1 to user1. The ``chowner``, ``chownfile``, and ``chownf`` commands are not valid.

9. **Answer:**  b. who

**Explanation:** 

    The ``who`` command is used to display information about users who are currently logged in. The ``users`` command is used to display the users who are currently logged in. The ``whoami`` command is used to display the current user. The ``w`` command is used to display information about users who are currently logged in and what they are doing.


10. **Answer:** c. lsof and d. netstat

**Explanation:**  

    c. lsof

    You can use it with the -i option followed by the port number to check if the port is in use. For instance:
    css
    
    .. code-block:: bash

        lsof -i :80
        # This would check if port 80 is in use.

    d. netstat

    This command displays network connections, routing tables, interface statistics, masquerade connections, etc. To check if a specific port is in use, you can use:

    .. code-block:: bash

        netstat -tuln | grep :80
        # This would check if port 80 is in use.
    
    From the provided options, the correct answers are lsof and netstat. However, if you were looking for a single answer, I'd lean towards ``netstat`` as it's more commonly associated with this task.

11. **Answer:** a. df

**Explanation:**

    The ``df`` command is used to display disk usage. It displays the amount of disk space available on the file system. The ``du`` command is used to display disk usage for a directory. The ``ls`` command is used to list files in a directory. The ``cd`` command is used to change directories.

12. **Answer:** d. free

**Explanation:**

    The ``free`` command is used to display memory usage. It displays the amount of free and used memory in the system. The ``df`` command is used to display disk usage. The ``du`` command is used to display disk usage for a directory. The ``ls`` command is used to list files in a directory.

13. **Answer:** d. top

**Explanation:** 

    The ``top`` command is used to display information about processes and system resources. It displays the processes that are currently running and their resource usage. The ``df`` command is used to display disk usage. The ``du`` command is used to display disk usage for a directory. The ``ls`` command is used to list files in a directory.

14. **Answer:** d. netstat

**Explanation:** 

    netstat (Network Statistics) displays active connections, listening ports, routing tables, interface statistics, and more. While it does not show the actual "bandwidth" being used, it provides information about active network connections.

    The other options are related to file and directory operations:

    a. df - Used to display disk space usage of file systems.
    b. du - Used to estimate file space usage.
    c. ls - Used to list directory contents.

    So, out of the provided options, the answer is:

    d. netstat

    However, if you're specifically interested in bandwidth usage or throughput, you'd want to use tools like ``iftop``, ``nload``, or ``bmon``, which are not listed among your choices.

15. **Answer:** b. systemctl disable

**Explanation:** 

    The ``systemctl disable`` command is used to disable a service. It prevents the service from starting automatically at boot time. The ``systemctl stop`` command is used to stop a service. The ``systemctl remove`` command is used to remove a service. The ``systemctl delete`` command is used to delete a service.

16. **Answer:** a. systemctl status

**Explanation:**

    The ``systemctl status`` command is used to check if a service is running. It displays the status of a service. The ``systemctl check`` command is used to check the configuration of a service. The ``systemctl test`` command is used to test a service. The ``systemctl run`` command is used to run a service.
