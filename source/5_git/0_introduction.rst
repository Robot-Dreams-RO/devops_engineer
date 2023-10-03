################
5.0 Introduction
################

============
What is GIT?
============

Git is a distributed version control system. This means that a local clone of the project is a complete version control repository. These fully-functional local repositories make it easy to work offline or remotely. Developers commit their work locally, and then sync their copy of the repository with the copy on the server. This paradigm differs from centralized version control where clients must synchronize code with a server before creating new versions of code.

Every time work is saved, Git creates a **commit**. A commit is a snapshot of all files at a point in time. If a file has not changed from one commit to the next, Git uses the previously stored file.

**Branches**, which are lightweight pointers to work in progress, manage this separation. Once work created in a branch is finished, it can be merged back into the team's main (or trunk) branch.

=================
Connect to GitHub
=================

There are 2 ways to log in to GitHub:

* keys

* credentials (username and password)

Generate the key from your local machine and upload it to GitHub

.. code-block:: bash

  # In a DevOps environment we want to have as much information as possible
  ssh-keygen -t ed25519 -C "user@hostname"

========================
What exactly is ed25519?
========================

ed25519 is a new cryptography solution that provides the Edwards-curve Digital Signature Algorithm (EdDSA).

Similarly, not all software solutions currently support ed25519, but SSH implementations in most modern operating systems do.

-------------------------------
Why is ed25519 Key a Good Idea?
-------------------------------

When compared to the most common type of SSH key - RSA - ed25519 offers several interesting advantages:

    #. It is faster to generate and verify

    #. it is more secure collision resilience - that is, it is more resistant to hash-function collision attacks (types of attacks where large numbers of keys are generated with the hope of getting two different keys to have matching hashes)

    #. The keys are smaller, which means they are easier to transfer and copy/paste.

Read the newly generated key

.. code-block:: bash

    cat ~/.ssh/id_ed25519.pub

    # Upload the newly generated key to GitHub
    # https://github.com/settings/keys

    # Clone projects on your local machine

We will learn how to use the terminal, console version of git, how to use vim, and fix merge conflicts.

.. code-block:: bash
  
    # install git
    sudo apt install git

    # verify that git is installed
    git --version

    # change directory to home
    cd ~

    # creates a directory
    mkdir sandbox 
    cd sandbox
    
    # download the project

    git clone git@github.com:Robot-Dreams-RO/devops_engineer.git 
    cd git # change directory to project
    git branch -a # check what branches are available
    git checkout master # move to a different branch
    git checkout develop # move back to develop  
    git checkout -b feature/yourName # create a new branch with your name

===========================
1. Create a scripts project
===========================

Create a new project in your userspace named ``scripts``. Press on the Kitten on the top left then new.

.. code-block:: bash

    # Clone the new project
    git clone git@github.com:<USER>/scripts.git

    # Change the directory to your new repository
    cd scripts
 
    # Config GitHub information
    git config --global user.email "MAIL"
    git config --global user.name "<USER>"

    # Create a new script
    echo "echo Hello World!" > HelloWorld

    # Add Hello World in it
    # Check the files that will be pushed to remote
    git status
    
    # Add the HelloWorld in git staging
    git add HelloWorld

    # Add a commit message
    git commit -m "Initial commit"

    # Push the code
    git push
