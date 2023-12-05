##############
7.2 Python CLI
##############

.. note::

    A Python CLI (Command Line Interface) is a type of software application that provides a text-based interface for interacting with the computer's operating system. The user interacts with the application using a terminal or command prompt, typing commands and receiving output in text form.

Python is a popular language for developing CLIs because of its simplicity, readability, and powerful libraries. With Python, you can quickly create a CLI that provides a convenient way to automate tasks, access data, or control other software applications.

A Python CLI typically consists of the following components:

    #. **Argument parsing**: The CLI takes user-supplied input in the form of command-line arguments, which are passed to the program when it is executed. A library such as argparse or click is used to parse these arguments and extract meaningful information from them.
    #. **Main logic**: The main logic of the CLI is written in Python and implements the desired functionality. This logic can include reading and writing files, making API calls, or performing calculations.
    #. **Output**: The CLI provides output in the form of text printed to the terminal. This output can be formatted in various ways to provide information to the user or to be consumed by other programs.

By using Python to create a CLI, you can provide a convenient and efficient interface for performing tasks and accessing information. Whether you're automating a workflow, analyzing data, or controlling a system, a Python CLI can be an effective tool.

================
Example 1 - code
================

A Python CLI that uses the Click library to print a random string:

Create a directory for your project:

    ::

        cli
        ├── init.py
        └── random_string_cli.py
        tests
        └── test_random_string_cli.py

Update the ``random_string_cli.py`` file with the following code:

.. code-block:: python

    """
    Simple program that generates a random string based on the selected length.
    """
    import random
    import string
    import click


    @click.command()
    @click.option("--string_length", "-l", default=10, help="Number of characters.")
    def random_string(string_length=10):
        """Simple function that generates a random string based on the selected length."""
        random_str = "".join(
            random.choices(string.ascii_letters + string.digits, k=string_length)
        )
        click.echo(random_str)


    if __name__ == "__main__":
        random_string()


This CLI uses the ``click`` library to create a command-line interface. The ``click.command ``decorator is used to define the ``random_string`` function as a command-line command. 
The ``random_string`` function generates a random string using the ``random.choices`` method from the random module, which selects 10 random characters from a string composed of letters and digits. 
The ``click.echo`` function is then used to print the random string to the console.

+++++++++++++++++++++++++++++++++++++++
Example 1 - Building code with setup.py
+++++++++++++++++++++++++++++++++++++++

Building code in Python refers to the process of writing, testing, and packaging software written in the Python programming language. The following steps are involved in building code in Python:

    #. Write the code: The first step in building code in Python is writing the code itself. This involves writing the desired functionality in Python, using the language's syntax and libraries.
    #. Test the code: Once the code has been written, it is important to test it to ensure that it behaves as expected. This can involve writing unit tests, integration tests, or end-to-end tests to verify the code's behavior.
    #. Package the code: If the code is intended to be used by others, it is typically packaged into a distribution package, such as a .tar.gz file, which makes it easy to distribute and install.
    #. Deploy the code: Finally, the code can be deployed, either to a production environment, such as a web server or a cloud instance or to a development environment, such as a local machine or a virtual environment, for testing and development.

Building code in Python is made easy by the language's simplicity, readability, and powerful libraries. With the right tools and processes in place, you can quickly and easily build and deploy robust, scalable code in Python.

An example of a ``setup.py`` file that installs the previous Python CLI code:

.. code-block:: python

    from setuptools import setup, find_packages

    setup(
        name='random_string_cli',
        version='0.1',
        packages=find_packages(),
        install_requires=[
            'click',
        ],
        entry_points={
            'console_scripts': [
                'random_string_cli = cli.random_string_cli:random_string',
            ],
        },
    )

This ``setup.py`` file is used to package and distribute the Python CLI as a package that can be installed using the ``pip`` package manager. 
The ``setup`` function is used to define the package details, including the name, version, and dependencies. The ``install_requires`` parameter is used to specify the required dependencies, in this case, the ``click`` library. 
The ``entry_points`` parameter is used to define the console scripts, which are command-line executables that can be installed and run as standalone commands. In this example, the random_string function from the random_string_cli package is defined as a console script with the name random_string.

+++++++++++++++++++++++++++++++++++++
Example 1 - Building code with poetry
+++++++++++++++++++++++++++++++++++++

To build the above Python CLI using the poetry package management and build tool, you would need to follow these steps:

    #. Install ``poetry``: install it using ``pip`` by running the command ``pip install poetry``.

    #. Initialize a new ``poetry`` project: Navigate to the directory where you want to create your new project and run the command ``poetry init``. This will create a new poetry project and generate a ``pyproject.toml`` file.

    #. Add dependencies: In this case, you will need to add the click library as a dependency. You can do this by adding the following line to your pyproject.toml file:

    .. code-block:: python

        [project]
        name = "random_string_cli"
        version = "0.0.2"
        license = {file = "LICENSE"}
        description = "A small python cli that generates a random string"
        authors = [{name = "skillab", email = "admin@skillab.com"}]

        dependencies = ["click"]
        requires-python = ">=3.10"

        [project.scripts]
        random_string_cli = "cli.random_string_cli:random_string"

        [build-system]
        requires = ["setuptools>=50", "wheel"]
        build-backend = "setuptools.build_meta"

    #. Write your code: Write the code for your CLI in a new Python file, making sure to import click and use it to create your command line interface.

    #. Package your code: Use the poetry build command to package your code into a distribution package that can be installed by others.

    #. Install and run your CLI: You can now install your CLI using the poetry install command, and run it by executing the appropriate command in your terminal.

By using poetry to manage your dependencies and build your code, you can streamline your development process and ensure that your code is easily installed and run by others.

++++++++++++++++++++++++
Example 1 - Testing code
++++++++++++++++++++++++

PyTest is a testing framework for Python that makes it easy to write and run tests for your code. The basic structure of a test written using PyTest is as follows:

    #. Write a test function: A test function is a Python function that verifies the behavior of a specific piece of code. The test function uses the assert statement to verify that the code under the test behaves as expected.

    #. Name the test function: PyTest automatically discovers and executes test functions whose names start with ``test_``.

    #. Run PyTest: To run PyTest, simply execute the pytest command in the directory containing your test functions. PyTest will discover and run all test functions, reporting any failures or errors.

    #. Verify test results: PyTest will report the results of the tests, indicating which tests passed and which tests failed. If a test fails, PyTest will report the values of the actual and expected results.

In general, PyTest makes it easy to write tests for your code by providing a simple, expressive syntax and powerful test discovery and execution features. By using PyTest, you can quickly and easily verify the behavior of your code, ensuring that changes and additions do not break existing functionality.

.. code-block:: python

    from click.testing import CliRunner
    from cli.random_string_cli import random_string

    runner = CliRunner()

    def test_random_string():
        result = runner.invoke(random_string)
        assert result.exit_code == 0
        assert len(result.output.strip()) == 10

This test uses ``PyTest`` to test the random_string function from the random_string_cli module. The test function, test_random_string, uses the assert statement to verify that the result is a string, that its length is 10, and that it only contains characters from the set of letters and digits. PyTest automatically discovers and executes this test function when you run the pytest command in the same directory as this file. If any of the assert statements fail, PyTest will report the failure, including information about the values that were expected and actual.

================
Example 2 - code
================

A Python CLI that uses the Click library to print information about the system.

You can find the code in ``source_code/python/cli``:

Directory structure for the Python CLI code:

    ::

        devops_cli
        ├── init.py
        ├── cmds.py
        └── devops_cli.py
        tests
        └── test_devops_cli.py
        requirements.txt
        setup.py

Create a new virtual environment for the project:

    .. code-block:: bash

        python3 -m venv venv

Activate the virtual environment:

    .. code-block:: bash

        source venv/bin/activate

Install the required dependencies:

    .. code-block:: bash

        pip install -r requirements.txt

To install the code in the location where we have ``setup.py ``file, run the following command: ``pip install -e .`` (-e stands for editable - it means that if you make changes to the code, you don't need to reinstall it)

To lint the code, run the following command: ``pylint .`` or ``flake8 .``

To check the static code analysis, run the following command: ``mypy .``

To run the unit tests, run the following command: ``pytest .``

=======================
Python directory layout
=======================

There are 2 directory structure alternative: ``src layout`` vs ``flat layout``.

- ``src layout``:
    
    ::

        .
        ├── README.md
        ├── noxfile.py
        ├── pyproject.toml
        ├── setup.py
        ├── src/
        │    └── package_name/
        │       ├── __init__.py
        │       └── module.py
        └── tests/

- ``flat layout``

    ::
        
        .
        ├── README.md
        ├── noxfile.py
        ├── pyproject.toml
        ├── setup.py
        ├── package_name/
        │   ├── __init__.py
        │   └── module.py
        └── tests/
