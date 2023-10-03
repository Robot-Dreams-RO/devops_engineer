##################
1. Getting started
##################

.. image:: ../diagrams/github_actions.drawio.png
  :alt: A diagram showing schematically how a Github Actions workflow is triggered and executed.
  :width: 1000 px

============================
Creating your first workflow
============================

1. Create a ``.github/workflows`` directory in your repository on GitHub if this directory does not already exist.

2. In the ``.github/workflows`` directory, create a file named ``hello_world.yml``.

3. Copy the following YAML contents into the ``hello_world.yml`` file:

.. code-block:: yaml

    name: Hello World
    run-name: ${{ github.actor }} is testing out GitHub Actions
    on: 
        - push
        - workflow_dispatch
    jobs:
    Explore-GitHub-Actions:
        runs-on: ubuntu-latest
        steps:
        - run: echo "The job was automatically triggered by a ${{ github.event_name }} event."

        - run: echo "This job is now running on a ${{ runner.os }} server hosted by GitHub!"

        - run: echo "The name of your branch is ${{ github.ref }} and your repository is ${{ github.repository }}."

        - name: Check out repository code
            uses: actions/checkout@v4

        - run: echo "The ${{ github.repository }} repository has been cloned to the runner."

        - run: echo "The workflow is now ready to test your code on the runner."

        - name: List files in the repository
            run: |
            ls ${{ github.workspace }}

        - run: echo "This job's status is ${{ job.status }}."

More variables can be found in the `GitHub Actions context and expression syntax for GitHub Actions <https://docs.github.com/en/actions/reference/context-and-expression-syntax-for-github-actions>`_.
