####
TODO
####

======
Task 1
======

On the PostgreSQL instance:
    #. create a new table AWESOME_CAR with columns ID, MAKE, MODEL, YEAR, COLOR, and ENGINE.
    #. insert 5 different lines into the table.
    #. select only black cars from the table that are newer than 2000.

======
Task 2
======

Based on `docker_examples/deploy_webserver` update the ``index.html`` with your name, job, age, hobby, and favorite picture.

======
Task 3
======

Create a Dockerfile based on a ``Fedora`` that:

#. create a user: ``docker_user`` that is part of ``docker_group`` with UID and GID ``7007``
#. create the following directory structure:

.. code-block:: sh

    ├── main_directory
        ├── secondary_directory_1
        └── secondary_directory_2
            └── hello_world.py

#. where ``main_directory`` is owned by ``docker_user`` and ``root`` and the rest only by ``docker_user`` and ``docker_group``
#. add hello world in the python script
#. run script ``hello_world.py``

======
Task 4
======

Based on the docker-compose example:
- add another route ``/health`` that will give you status code 200
- update default route ``/`` based use the `adjective` and `name` from ``random_name.py`` to generate a random string next to the number of times you've visited the website.
- update the  ``/python ``to load the data from ``https://en.wikipedia.org/wiki/Python_(genus)`` and print a random python.