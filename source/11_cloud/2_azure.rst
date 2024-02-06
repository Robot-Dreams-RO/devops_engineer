##########
11.2 Azure
##########

.. note::

    Azure is a cloud computing platform and service offered by Microsoft. It provides a wide range of cloud-based services and solutions, including infrastructure as a service (IaaS), platform as a service (PaaS), and software as a service (SaaS) offerings.

Azure allows businesses and individuals to build, deploy, and manage applications and services in the cloud, using a range of programming languages, frameworks, and tools. Azure supports various operating systems, including Windows, Linux, and macOS, and can be used to develop applications for web, mobile, desktop, and IoT devices.

Azure provides a comprehensive set of services, including virtual machines, containers, databases, storage, networking, and analytics. It also offers AI and machine learning services, DevOps tools, and integration with other Microsoft services such as Office 365, Dynamics 365, and Power BI.

Azure provides a global network of data centers and offers high availability and disaster recovery options to ensure the reliability and performance of applications and services. It also provides strong security and compliance capabilities, including built-in encryption, identity and access management, and compliance with various industry standards and regulations.

Azure is used by a wide range of businesses and organizations, including startups, government agencies, and Fortune 500 companies, to accelerate innovation, improve agility, and reduce costs.


.. note:: 
    
    We're not installing the cloud but we're installing some tools that will allow us to interact with the cloud.

=================
Install Azure CLI 
=================

.. note::

    azcli is a command-line tool for managing Azure resources.

Installation details can be found here https://learn.microsoft.com/en-us/cli/azure/install-azure-cli for WSL Ubuntu you can run ``curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash``

============
Install func
============

.. note::

    func is a command-line tool for managing Azure Functions. 

Installation details can be found here https://learn.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=v4%2Clinux%2Ccsharp%2Cportal%2Cbash for WSL Ubuntu:

.. code-block::

    curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

    sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg

    sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-$(lsb_release -cs)-prod $(lsb_release -cs) main" > /etc/apt/sources.list.d/dotnetdev.list'

    sudo apt-get update

    sudo apt-get install azure-functions-core-tools-4

=================
Install Terraform
=================

You can download the latest version of Terraform from the official website: https://www.terraform.io/downloads.html for WSL Ubuntu

.. code-block::

    wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
    echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

    sudo apt update && sudo apt install terraform

===============
Getting started
===============

An example of an Azure Function App that uses Flask and Swagger for API documentation.

Create a virtual environment and install the required packages:

.. code-block::
    
    # create a python virtual environment
    python -m venv venv

    # activate the virtual environment
    source venv/bin/activate

    # install the required packages
    pip install -r source_code/requirements.txt

Create a new Azure Functions project:

.. code-block::

    func init --worker-runtime python

Create a new Azure Functions HTTP Trigger:

.. code-block::

    func new --name robot_dreams --template "HTTP trigger"

Modify the ``requirements.txt`` file to include the required packages:

.. code-block::

    azure-functions
    fastapi


To test the function locally, start the Azure Functions Core Tools:

.. code-block::

    func start

Deploy the function in the previously created environment:

.. code-block::

    func azure functionapp publish func-robot-dreams-deploy
