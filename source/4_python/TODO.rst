########
10. TODO
########

======
Task 1
======

Create a script ``wikipython.py`` that:

    - reads a Wikipedia page: ``https://en.wikipedia.org/wiki/Python_(genus)`` (use ``requests`` command)
    - extracts Species elements - python name (what kind of pythons are there) (use ``BeautifulSoup``)
    - save the output the to a new file
    - append to the new file the last line that is the count of species

======
Task 2
======

Create script ``weather.py`` that gives you the weather from ``curl`` https://wttr.in/(location)

    - the location will be read from the keyboard - for example ``weather Bucharest``
    - test that location is valid using ``https://nominatim.openstreetmap.org/search?format=json&q=`` + location

======
Task 3
======

Create a health check script ``healthCheck.py`` that looks at:

    - date and time using ``import datetime``
    - the uptime of the machine using ``uptime``
    - how much disk ``df`` and memory usage ``free`` using ``import psutil``