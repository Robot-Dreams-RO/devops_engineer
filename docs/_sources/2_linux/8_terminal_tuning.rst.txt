###################
2.8 Terminal tuning
###################

=======
Aliases
=======

The alias command makes it possible to launch any command or group of commands (with arguments, options, or redirection) by entering a pre-set string.

Update user profile ``.bashrc``, ``bash_profile`` or ``.profile``

.. code-block:: bash

    # Add arguments to a command that exists
    alias ll='ls -ltrha --color=auto'

    # Add arguments to a command that exists
    alias ls='ls -ltrha --color=auto'

    # Redirect the old application to the new one
    alias vi='vim'

    # Correct typing errors
    alias exot='exit'

    # Correct typing errors
    alias clera='clear'

    # Link more commands under one
    alias qpositive='history -c && history -w && exit'

    alias bing='git push'
    alias bang='git status && git add --all && git commit -m'

    # Go to the sandbox
    alias duck='cd /home/devx/sandbox'

    # Activate python virtual environment
    alias qqqRunVEnv='. venv/bin/activate'

    # Create python virtual environment
    alias eeeCreateVEnv='python3 -m venv venv'

    # Run last command as root
    alias zzz='sudo $(history -p \!\!)'

========
The fuck
========

``TheFuck`` is a magnificent app that corrects errors in previous console commands.

.. code-block:: bash

    # create Python environment
    python3 -m venv venv

    # source Python environment
    . venv/bin/activate

    # install thefuck python library
    pip install thefuck

Update user profile ``.bashrc``, ``bash_profile`` or ``.profile``

.. code-block:: bash

    eval $(thefuck --alias FUCK)

===========================
Run sudo without a password
===========================

Update the ``/etc/sudoers`` file:

.. code-block:: bash

    %sudo   ALL=(ALL:ALL) ALL

to

.. code-block:: bash

    %sudo   ALL=(ALL:ALL) NOPASSWD:ALL
