#######################
8.3 Working with Docker
#######################

.. note::

    We rarely run docker commands from the cli, but when we do use ``docker help`` to get more information

==================================
Detached vs Foreground/Interactive
==================================

Use the ``-d=true`` or plain ``-d`` option to launch a container in detached mode(in background). Unless you optionally supply the ``—rm`` option, containers started in detached mode by default terminate when the root process used to operate the container terminates.

Use the ``-i`` to launch a container in interactive mode.

We're run multiple time this command: run a interactive bash session in a new fedora container.

.. code-block:: bash

    docker run --name fedora -it fedora bash

=======================
Working with docker cli
=======================

.. code-block:: sh

    # list available images
    docker images

    # list available containers
    docker ps

    # remove container
    docker rm
    
    # remove images
    docker rmi

-------------------
Deploy a database
-------------------

The name of the image has to be unique, we can run it with ``--name`` to specify something relatable.

.. code-block:: sh

    docker run --name localPostgres -p 55432:5432 -e POSTGRES_USER=postgresUser -e POSTGRES_PASSWORD=postgresPass -e POSTGRES_DB=postgresDB -d postgres

    # --name = name of the container [ has to be unique ]
    # -p = port of the container [ we have to specify the mapping from outside to inside of the container external_port:internal_port ]
    # -e = environment variables
    # -d = detached mode

-----------------------
Connect to the database
-----------------------

Because we are running the Docker Desktop next to the WSL, we need to disconnect from WSL.

Install the PostgreSQL extension from Extension tab: ``PostgreSQL by Chris Kolkman``.

From PostgreSQL explorer (is now a tab) - Add Connection.

.. code-block:: sh

    hostname: localhost
    postgresql user: postgresUser
    postgresql pass: postgresPass
    port: 55432

    Use an ssl connection - no - Standard Connection

    Select DB postgresDB

    Display name: localPostgres

Right click on the localPostgres -> New Query. You can copy the entire script and run parts of it by selecting and pressing F5.

.. code-block:: sql

    CREATE TABLE MARVEL(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    POWER          TEXT
    );

    INSERT INTO MARVEL (ID, NAME, AGE, POWER)
    VALUES (1, 'IRONMAN', 40, 'RICH');
    INSERT INTO MARVEL (ID, NAME, AGE, POWER)
    VALUES (2, 'CAPTAIN AMERICA', 30, 'SUPERHUMAN POWER');
    INSERT INTO MARVEL (ID, NAME, AGE, POWER)
    VALUES (3, 'THOR', 1200, 'MASTER OF THUNDER');
    INSERT INTO MARVEL (ID, NAME, AGE, POWER)
    VALUES (4, 'HULK', 45, 'IMPOSSIBLE TO KILL');

    SELECT * FROM MARVEL;
