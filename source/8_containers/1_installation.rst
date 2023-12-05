########################
8.1 Windows installation
########################

.. warning::

    Commercial use of Docker Desktop in larger enterprises (more than 250 employees OR more than $10 million USD in annual revenue) requires a paid subscription.
    You can use it at home, but at work ask your IT Department.

======================
Virtualization backend
======================

There are 2 backends available:

    1. WSL 2
    
        The Windows Subsystem for Linux enables programmers to run a GNU/Linux environment directly on Windows, unaltered, without the burden of a conventional virtual machine or dual boot setup. This includes the majority of command-line tools, utilities, and applications. 
        
        You can select multiple from multiple Linux distributions.
        
    2. Hyper-V
        Microsoft's hardware virtualization solution is called Hyper-V.

        It enables you to build and use a virtual machine, which is a software representation of a computer. Each virtual machine runs an operating system and applications, acting like a full-fledged computer.

        Virtual machines give you more flexibility and are a more effective method to utilize hardware than just running one operating system on actual hardware when you need computing resources.You can operate several virtual machines on the same hardware at once because Hyper-V runs each virtual machine in its own isolated environment.

==================
Installation steps
==================

    1. Download Docker Desktop from: https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe, then
    2. Depending on the backend you choose, make sure the Use WSL 2 instead of Hyper-V (You won't be able to choose which backend to use if your system only supports one of the two possibilities.)
    3. To approve the installer and continue with the installation, follow the directions on the installation wizard.
    4. To finish the installation process after a successful installation, click Close.