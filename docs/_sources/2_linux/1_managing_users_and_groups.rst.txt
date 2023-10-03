#############################
2.1 Managing Users and Groups
#############################

For an authorized person to gain access to the system, a user account must be created on the system. User and group account information is stored in several files:

.. code-block:: bash

    # User and group information
    /etc/passwd

    # Encrypted user passwords
    /etc/shadow

    # Group information
    /etc/group

    # Group passwords
    /etc/gshadow

===========
/etc/passwd
===========

The ``/etc/passwd`` file contains all user's properties. Each line contains information about one user account. There are seven fields per line entry separated by a colon (:).

.. code-block:: bash

    user_name:x:UID:GID:comments:home_directory:shell

    # user_name: `/^[a-z0-9-*]+$/`. Should not use uppercase letters or special characters
    # x: password placeholder
    # UID: a unique number. UIDs between 0 and 999 are reserved for system accounts
    # GID: a number that corresponds with a group entry in /etc/group
    # comments: info about the user
    # home_directory: the default location is /home/user_name
    # shell: user's default shell

===========
/etc/shadow
===========

This file stores the encrypted user's password along with other info.

.. code-block:: bash

    user_name:encrypted_passwords:lastchg_days:min_days:max_days:warn_days:inactive_days:disabled_days:

    # user_name: `/^[a-z0-9-*]+$/`. Should not use uppercase letters or special characters
    # encrypted_passwords: May be empty. An exclamation mark shows that the user is locked
    # lastchg_days: number of days in epoch time since the password was changed
    # min_days: minimum number of days that must pass before the user can change the passwords
    # max_days: maximum number of days before the user gets password expiration warnings
    # warn_days**: number of days for which the user gets password expiration warnings
    # inactive_days: maximum number of days for user inactivity
    # disabled_days: number of days in epoch time after which the account expires

Most of the above parameters can be changed with **password**, **usermod**, and/or **chage** commands.

==========
/etc/group
==========

This file contains group information. Every user must be a member of at least one group, which is called *the primary group*. Additional groups may be created and users assigned to them.

.. code-block:: bash

    group_name:x:GID:user_list

    # group_name: a unique group name
    # x: password placeholder. Usually, group passwords are not used. It may contain an encrypted password
    # GID: the group ID
    # user_list: a comma-delimited list of users assigned to the group. The user's primary group is defined in /etc/password

===================
Configuration files
===================

The files mentioned above contain only user and group information and attributes. There are additional files/directories that configure default values for various attributes.

.. code-block:: bash

    # default values for useradd command
    /etc/default/useradd

    # default values for groupadd command
    /etc/login.defs

    # default values for useradd command
    /etc/skel/

===============
User management
===============

Normally user management is done via an external application, but to understand the flow we will do them manually.

-----------------
Create a new user
-----------------

Create 2 new users: one unprivileged and one privileged that will be part of the unprivileged group.

.. code-block:: bash

    # create a user named unprivileged_user
    useradd unprivileged_user

    # check the unprivileged_user, we will see that is part of a group called unprivileged_user
    id unprivileged_user

    # create an user named privileged_user part of the unprivileged_user group
    useradd privileged_user -G unprivileged_user
    
    # check the privileged_user we will see that has 2 groups:
    # primary group: privileged_user
    # secondary group: unprivileged_user
    id privileged_user

Creating 3 new groups, 3 new users, and share access.

.. code-block:: bash

    # Get help for the groupadd command
    groupadd --help

    # Create 3 new groups: developers, operations, and devopsgroup
    groupadd developers
    groupadd operations
    groupadd devopsgroup

    # Get help for the useradd command
    useradd --help

    # Create 3 new users: dev, ops, and devops
    useradd dev
    useradd ops
    useradd devops

    # Get help for the usermod command
    usermod --help

    # Add devops user to the developers group, then append to the operations group
    usermod -G developers devops
    usermod -aG operations devops

    # Get help for the id command
    id --help

    # Check the devops user, we will see that has 3 groups: primary group: devops, secondary groups: developers, operations
    id devops

+++++++++++++++++++++++++++++++++++++++++
Set a password for the newly created user
+++++++++++++++++++++++++++++++++++++++++

.. code-block:: bash

    # Get help for the passwd command
    passwd --help

    # Set a password for the devops user
    passwd devops

    # Change user password expiry information
    chage --help

    # Change user password expiry information
    # -l: list password aging information
    chage -l devops

+++++++++++++++++++++++
Remove users and groups
+++++++++++++++++++++++

When removing users that are part of a group, pay attention.

.. code-block:: bash

    # Get help for the userdel command
    userdel --help

    # Remove the unprivileged_user
    userdel -r unprivileged_user

    # Remove the privileged_user
    userdel -r privileged_user

    # Get help for the groupdel command
    groupdel --help

    # Remove the unprivileged_user group
    groupdel unprivileged_user

    # Remove the privileged_user group
    groupdel privileged_user

====
TODO
====

1. create a user named *alice* with UID and GID set to *3001*
2. create a user named *bob* with home directory in */opt*
3. create a user named *john* with comment field set to *John Doe*
4. create a user named *minecraft* with:
    
    a. UID *9990*
    b. GID *9990*
    c. home directory in */usr/games*
    d. do not create the home directory
    e. no login privileges
    f. shell set to */bin/false*

5. set a password for alice
6. create a group named *datamanagement* with GID 9001
7. add *alice* and *bob* to the *billing* group
8. configure password aging for *alice* with **chage** command:
    
    a. password validity 31 days
    b. the user should receive warnings 7 days before password expiration

9. lock the *minecraft* account and password 
10. remove the *minecraft* account and home directory
11. remove the *minecraft* group
12. remove the *datamanagement* and *billing* group

.. warning::

    Passwords are like underwear. Change them often, don't share them, and don't leave them out for others to see.

=================
Solution to TODOs
=================

1. ``useradd alice -u 3001 -g 3001``
2. ``useradd bob -d /opt``
3. ``useradd john -c "John Doe"``
4. ``useradd minecraft -u 9990 -g 9990 -d /usr/games -m -s /bin/false``
5. ``passwd alice``
6. ``groupadd datamanagement -g 9001``
7. ``usermod -aG billing alice``
8. ``chage -M 31 -W 7 alice``
9. ``passwd -l minecraft``
10. ``userdel -r minecraft``
11. ``groupdel minecraft``
12. ``groupdel billing && groupdel datamanagement``