#########################
8.2 Running "Hello World"
#########################

Because Docker is installed next to the WSL we need to use **Windows Powershell**.

Running the ``wsl`` command with list and verbose arguments:

.. code-block:: bash

    wsl -l -v

we should see

.. code-block:: bash

    PS C:\Users\skillab> wsl -l -v
    NAME                   STATE           VERSION
    docker-desktop-data    Running         2
    Ubuntu                 Running         2
    docker-desktop         Running         2

To see if the docker is available we can run

.. code-block:: bash
    
    PS C:\Users\skillab> docker --help

    Usage:  docker [OPTIONS] COMMAND

    A self-sufficient runtime for containers

To test if the Docker is installed correctly we can run

.. code-block:: bash

    docker run hello-world

Docker uses isolated containers to run its processes. A process that runs on a host is called a container. The host could be local or remote. When a user runs the ``docker run`` command, a container process is launched that is isolated from the host by having its own file system, networking, and isolated process tree.
