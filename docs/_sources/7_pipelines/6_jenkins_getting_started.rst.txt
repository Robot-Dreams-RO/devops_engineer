###################
7.6 Getting started
###################

.. image:: ../diagrams/jenkins_logo.png
  :alt: Jenkins logo

===================
Run Jenkins locally
===================

1. Run a Jenkins main server using a Docker container with the following command:

.. code-block:: bash

    docker run --detach --name jenkins --publish 127.0.0.1:8080:8080 --volume jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11

On the first run Jenkins automatically generates a password for the admin user and prints it to the logs it generates and saves it in the ``/var/jenkins_home/secrets/initialAdminPassword`` location.

2. Get the initial password from the Jenkins own logs using the following command:

.. code-block:: bash

    docker logs jenkins

3. Next step for our purpose is to choose to install the recommended plugins. Note that this action can take a few minutes until it is finished.

4. Create First Admin User.

5. Start use your local Jenkins instance.


===============
Getting started
===============

-----------------------------
Configure your first pipeline
-----------------------------

Create a new git repository with the bellow ``hello_world`` app.

``main.py:``

.. code-block:: python

    from fastapi import FastAPI

    app = FastAPI()

    @app.get("/")
    async def read_root():
        return {"msg": "Hello world"}

    @app.get("/name/{name}")
    async def read_item(name: str):
        return {"msg": f"Hello {name}"}


``test_main.py:``

.. code-block:: python

    from fastapi.testclient import TestClient
    from main import app

    client = TestClient(app)

    def test_read_root():
        response = client.get("/")
        assert response.status_code == 200
        assert response.json() == {"msg": "Hello world"}

    def test_read_item():
        response = client.get("/name/Ionescu")
        assert response.status_code == 200
        assert response.json() == {"msg": "Hello Popescu"}


``requirements.txt``

.. code-block:: bash

  fastapi
  uvicorn
  pylint
  httpx
  pytest
  requests

Test the app by running:

.. code-block:: bash

  pytest

  pylint main.py

  pylint test_main.py

==================================
Create your first Jenkins pipeline
==================================

1. Set up a Jenkins Job:

Create New Job:

Log in to Jenkins and click on "New Item".
Enter a name for your job and select the "Pipeline" type.
Configure the Job:

In the job configuration, scroll down to the "Pipeline" section.
Choose "Pipeline script" as the definition.
You can use a Jenkinsfile to define the pipeline or directly write the pipeline script in the Jenkins job configuration.

2. Define the Jenkins Pipeline Script:

Here's an example of a Jenkins pipeline script that performs the FastAPI tests:

.. code-block:: groovy

    pipeline {
        agent any

        stages {
            stage('Checkout') {
                steps {
                    // Check out code from your repository
                    git 'https://github.com/your-username/your-repo.git'
                }
            }

            stage('Install dependencies') {
                steps {
                    // Install required dependencies
                    sh 'pip install -r requirements.txt'
                }
            }

            stage('Run tests') {
                steps {
                    // Run tests using pytest
                    sh 'pytest'
                }
            }
        }
    }
    

Ensure to replace the repository URL (https://github.com/your-username/your-repo.git) with your actual repository containing the FastAPI application code.

3. Save and Build the Jenkins Job:

Save the Jenkins job configuration.
Trigger a build by clicking on "Build Now" to test the job.

4. View Test Results:

Once the build is complete, you can check the test results in the Jenkins console output.
Jenkins will display the status of each stage and the test results.
