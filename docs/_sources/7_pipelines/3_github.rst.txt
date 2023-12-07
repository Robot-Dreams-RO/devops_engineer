##########
7.3 GitHub 
##########

.. note::

    GitHub Actions is a continuous integration and continuous delivery (CI/CD) platform that enables developers to automate their software development workflows directly from their GitHub repository.

With GitHub Actions, developers can create custom workflows, called "actions," that automate tasks such as building, testing, and deploying code. These workflows can be triggered by events such as code pushes, pull requests, or scheduled cron jobs.

Topics to be covered in this chapter:

    - Github Actions workflows and actions
    - Github Actions runners and self-hosted runners
    - Github Actions secrets
    - Github Actions artifacts
    - Github Actions environments
    - Jobs and steps

Some key features of GitHub Actions include:

    #. Automated Workflows: Automating tasks such as building, testing, and deploying code with custom workflows.
    #. GitHub Integration: Triggering workflows from GitHub events, such as code pushes or pull requests, and accessing GitHub data in workflows.
    #. Third-Party Integrations: Integrating with popular tools and services, such as Docker, Kubernetes, AWS, and more.
    #. Container-Based: Running workflows in isolated containers, providing a clean and consistent environment for each job.
    #. Community-Driven: Access to a large library of open-source actions, as well as the ability to share and reuse custom actions within the GitHub community.

GitHub Actions provides a simple and efficient way to automate software development workflows, making it easier to build, test, and deploy code directly from GitHub.

.. code-block:: bash

    # This workflow will install Python dependencies, run tests, and lint with a single version of Python
    name: Python application

    on:
    push:
        branches: [ "main" ]
    pull_request:
        branches: [ "main" ]

    permissions:
    contents: read

    jobs:
    test_python:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v3

        - name: Set up Python 3.10
        uses: actions/setup-python@v3
        with:
            python-version: "3.10"
        
        - name: Install dependencies
        working-directory: source_code/pipelines
        shell: bash
        run: |
            python -m pip install --upgrade pip
            pip install -r requirements.txt
        
        - name: Lint with pylint
        working-directory: source_code/pipelines
        shell: bash
        run: pylint cli/

        - name: Check with mypy
        working-directory: source_code/pipelines
        shell: bash
        run: mypy cli/
        
        - name: Test with pytest
        working-directory: source_code/pipelines
        shell: bash
        run: pytest

A GitHub Actions workflow is composed of a series of events and actions.

    #. Events: Events are triggers that start a workflow, such as a push to the repository, opening a pull request, or scheduling a cron job.

    #. Actions: Actions are individual tasks that make up the workflow, such as checking out code from the repository, building and testing code, or deploying code to a production environment.

A workflow is defined in a YAML file in the .github/workflows directory of a GitHub repository. The structure of a GitHub Actions workflow typically includes:

    #. Name: A unique name for the workflow that identifies it in the GitHub Actions interface.

    #. On: The event that triggers the workflow, such as a push to the repository or opening a pull request.

    #. Jobs: One or more jobs that make up the workflow, each with its own set of steps.

    #. Steps: The individual tasks, or steps, that make up a job. Steps can be individual shell commands or calls to predefined actions from the GitHub Actions marketplace or other sources.

    #. Conditionals: Optional logic that determines whether a step or job should be run, based on conditions such as the success or failure of previous steps or the value of environment variables.

This workflow runs whenever the code is pushed to the main branch of the repository. It consists of one job, "build," that runs on an Ubuntu virtual machine and performs four steps: checking out the code, setting up Node.js, installing dependencies, and building and testing the code.

====================
Workflows vs Actions
====================

A workflow is a configurable automated process made up of one or more jobs. Workflows are defined in YAML files, which are stored in the ``.github/workflows`` directory of a repository.

An action is a reusable unit of code that can be used in a workflow. Actions are the smallest portable building block of a workflow. Actions can be written in JavaScript, TypeScript, or any other language that can be packaged in a Docker container.

A workflow can use actions defined in the same repository, a public repository, or a published Docker container image.

===================
Directory structure 
===================

1. GitHub Actions workflow

    ::

        .github/workflows/
        ├── build.yml
        └── deploy.yml

2. GitHub Actions action

    ::

        .github/actions/actionName
        ├──action.yml
        ├── Dockerfile
        ├── index.js
        └── package.json

===============
Workflow syntax
===============

A workflow is defined in a YAML file in the ``.github/workflows`` directory of a GitHub repository.

The structure of a GitHub Actions workflow typically includes:

    #. **Name**: A unique name for the workflow that identifies it in the GitHub Actions interface.
    #. **On**: The event that triggers the workflow, such as a push to the repository or opening a pull request.
    #. **Jobs**: One or more jobs that make up the workflow, each with its own set of steps.
    #. **Steps**: The individual tasks, or steps, that make up a job. Steps can be individual shell commands or calls to predefined actions from the GitHub Actions marketplace or other sources.
    #. **Conditionals**: Optional logic that determines whether a step or job should be run, based on conditions such as the success or failure of previous steps or the value of environment variables.

.. code-block:: yaml

    name: Python package

    # runs on push and pull request to master (keep in mind that most of the default branches would be blocked for pushing directly to master)
    on:
    push:
        branches: [ "master" ]
    pull_request:
        branches: [ "master" ]

    jobs:
    build:

        runs-on: ubuntu-latest
        strategy:
        fail-fast: false
        matrix:
            python-version: ["3.9", "3.10", "3.11"]

        steps:
        - uses: actions/checkout@v3
    
        - name: Set up Python ${{ matrix.python-version }}
        uses: actions/setup-python@v3
        with:
            python-version: ${{ matrix.python-version }}

        - name: Install dependencies
        run: |
            python -m pip install --upgrade pip
            python -m pip install flake8 pytest
            if [ -f requirements.txt ]; then pip install -r requirements.txt; fi

        - name: Lint with flake8
        run: |
            # stop the build if there are Python syntax errors or undefined names
            flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics
            # exit-zero treats all errors as warnings. The GitHub editor is 127 chars wide
            flake8 . --count --exit-zero --max-complexity=10 --max-line-length=127 --statistics

        - name: Test with pytest
        run: |
            pytest

or an workflow that uses the next action as a step:

.. code-block:: yaml

    name: Python application with Action

    on:
    push:
        branches: [ "main" ]
    pull_request:
        branches: [ "main" ]
    workflow_dispatch:

    permissions:
    contents: read

    jobs:
    test_python:
        runs-on: ubuntu-latest
        strategy:
        matrix:
            python-version: ["3.8", "3.9", "3.10", "3.11"]
        steps:
        - uses: actions/checkout@v3
        
        - uses: ./.github/actions/testing
        with:
            python-version:${{ matrix.python-version }}
  

=============
Action syntax
=============

An action is defined in a YAML file in the ``.github/actions/actionName/action.yaml`` directory of a GitHub repository.

The structure of a GitHub Actions action typically includes:

    #. **Name**: A unique name for the action that identifies it in the GitHub Actions interface.
    #. **Inputs**: A list of inputs that can be passed to the action.
    #. **Outputs**: A list of outputs that can be returned from the action.
    #. **Runs**: The runtime environment for the action, such as a Docker container or JavaScript runtime.
    #. **Steps**: The individual tasks, or steps, that make up the action. Steps can be individual shell commands or calls to predefined actions from the GitHub Actions marketplace or other sources.

.. code-block:: yaml

        name: 'Python Test Action'
        description: 'Action to setup, lint, type-check and test a Python application'

        inputs:
        python_version:
            description: 'Python version'
            required: true
            default: '3.11'

        runs:
        using: "composite"
        steps:
            - uses: actions/checkout@v3

            - name: Set up Python 3.10
            uses: actions/setup-python@v2
            with:
                python-version: ${{ inputs.python_version }}

            - name: Install dependencies
            working-directory: source_code/pipelines
            shell: bash
            run: |
                python -m pip install --upgrade pip
                pip install -r requirements.txt
            
            - name: Lint with pylint
            working-directory: source_code/pipelines
            shell: bash
            run: pylint cli/

            - name: Check with mypy
            working-directory: source_code/pipelines
            shell: bash
            run: mypy cli/
            
            - name: Test with pytest
            working-directory: source_code/pipelines
            shell: bash
            run: pytest


==========
Triggering
==========

There are several ways to trigger a workflow run:

    #. **Push**: A workflow can be triggered by a push to the repository. This is the default trigger for a workflow.
    #. **Pull Request**: A workflow can be triggered by a pull request to the repository.
    #. **Schedule**: A workflow can be triggered on a schedule, using cron syntax.
    #. **Webhook**: A workflow can be triggered by a webhook, such as a GitHub App.
    #. **External**: A workflow can be triggered by an external event, such as a Docker image being pushed to a registry.
    #. **On Demand**: A workflow can be triggered manually from the GitHub Actions interface.


==================
Workflow templates
==================

GitHub provides a number of workflow templates that can be used to quickly create a workflow for common tasks, such as building and testing code, deploying code to a production environment, or publishing a Docker image.

Workflow templates can be accessed from the GitHub Actions interface or from the GitHub Actions Marketplace.

==============
Github Secrets
==============

Managing secrets (passwords, tokens, certificates, keys) is a challenging problem in software development. Secrets can be used to grant access to resources, such as databases, APIs, and cloud services, and should be kept secure at all times.

GitHub Actions provides a way to securely store and access secrets, using the GitHub Actions interface or the GitHub API.

.. note::

    In most companies this feature is avoided because most of the time there are requirements to use a third party tool like Hashicorp Vault or Kubernetes Secrets to manage secrets inside of company network.

==============
Github Runners
==============

There are 2 types of workers:
    
    #. **GitHub-hosted runners**: GitHub provides a set of virtual machines that are pre-configured with a variety of software environments. These runners are available to use for free, each account has certain amounts of minutes per month.
    #. **Self-hosted runners**: You can host your own runners on your own machines, using a variety of operating systems and architectures. Self-hosted runners can be used for free, but require more setup and maintenance.
