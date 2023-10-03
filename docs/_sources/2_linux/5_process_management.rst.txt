######################
2.5 Process management
######################

#. a process is a unit for provisioning system resources
#. it is any program, application, or command that runs on the system
#. is created in memory in its own address space when a program, application, or command is initiated
#. each process has a parent process that spawns it
#. a single-parent process may have one or many child processes and passes many of its attributes to them at the time of their creation
#. each process is assigned a unique identification number, known as the process identifier (PID), which is used by the kernel to manage and control the process through its lifecycle
#. when a process completes its lifecycle or is terminated, this event is reported back to its parent process, and all the resources provisioned to it are then freed and the PID is removed

.. warning::

	Don't root and drink!

Learning about process management, we will start a misbehaving process:

.. code-block:: bash
	
	# Go to the sandbox
	cd ~/sandbox

	# Create a new file
	vim bad.py

	# Add this content
	!/usr/bin/env python3
	i = 0
	while i == 0:
		pass

	# Press i to insert
	# Then :wq

	# This program, when executed, runs in an infinite loop — not something you want running on your server.
	# Add execute permission
	chmod 750 bad.py
	# or
	chmod u+x bad.py
	
	# Run the program in the background
	./bad.py &
	
	# To find the process
	ps -ef | grep bad
	# or
	ps -ef | grep python
	# or
	pgrep -f bad

	# To kill the process
	kill PROCESS_ID

===============
kill vs kill -9
===============

The secure and appropriate method of ending a process is kill, often known as ``kill -TERM`` or ``kill -15``. It is comparable to properly turning off a computer.
The risky method of brutally murdering a process is ``kill -9``. It might corrupt the data and is similar to unplugging the power wire.

-------------------
Process Cheat sheet
-------------------

.. code-block:: bash

	# List all running processes
	ps aux

	# List all running processes in extra wide format
	# useful to display long commands that are trimmed by default
	ps auxww

	# Hierarchy list all running processes
	ps auxf

	# terminate process
	kill PID

	# forcefully terminate process
	kill -9 PID

	# returns a list of PIDs that have "keyword" in the command field
	pgrep -f "keyword"

	# terminates all PIDs that have "keyword" in the command field
	pkill -f "keyword"  

	# run "command" and send it in the background
	command &

	# detach command from tty and run it in the background
	# send stdout and sterr to the cmd.log file
	nohup command 2>&1 > cmd.log &

	# allows you to execute a command or program periodically and also shows your output on the screen which means that you will be able to see the program output in time. By default, watch re-runs the command/program every 2 seconds. The interval can be easily changed to meet your requirements.
	watch free -m
	
	# display commands sent to run in the background
	jobs

	# bring the last command sent to the background in the foreground
	fg

	# resume commands paused with CTRL-Z
	bg

.. warning::

	Thou shalt not kill -9

=========
Questions
=========

1. What is a process?

   a. A program that is running on the system
   b. A program that is running on the system and has a PID
   c. A program that is running on the system and has a parent process
   d. A program that is running on the system and has a parent process and a PID

2. What is a PID?

   a. A unique identification number assigned to a process
   b. A unique identification number assigned to a process by the kernel
   c. A unique identification number assigned to a process by the kernel that is used to manage and control the process through its lifecycle
   d. A unique identification number assigned to a process by the kernel that is used to manage and control the process through its lifecycle and is reported back to its parent process when the process completes its lifecycle or is terminated

3. What is the correct way to terminate a process?

   a. kill -9 PID
   b. kill -TERM PID
   c. kill PID
   d. kill -15 PID

4. What is the correct way to terminate a process that is not responding?

   a. kill -9 PID
   b. kill -TERM PID
   c. kill PID
   d. kill -15 PID

5. What is the correct way to terminate a process that is not responding and is not terminating with kill -9?

   a. kill -9 PID
   b. kill -TERM PID
   c. kill PID
   d. kill -15 PID

=======
Answers
=======

1. d
2. d
3. b
4. a
5. a