#################
11.4 CI/CD In AWS
#################

There are 2 ways to implement DevOps methodology in AWS:

- native AWS services
- third-party tools

==================  ====================  =============================
                    Native AWS Services   Third-Party Tools
==================  ====================  =============================
Code Repository     AWS CodeCommit        GitHub / GitLab              
Build Service       AWS CodeBuild         GitHub Actions / GitLab CI   
Deployment Service  AWS CodeDeploy        GitHub Actions / GitLab CI   
Pipeline Service    AWS CodePipeline      GitHub Actions / GitLab CI   
IaaS                AWS CloudFormation    terraform / openTofu / pulumi
==================  ====================  =============================

.. note::

    The third-party tools are more popular and have more features than the native AWS services.

.. note::

    If your company is fixed on staying within the AWS ecosystem, then you should use the native AWS services. If your company is wants to get best buck for the money, then you should use the third-party tools. If there is only a small chance to move to another cloud provider, then you should use the third-party tools.

In this course, we've always used open source tools that can be used on any cloud provider. We've used: GitHub, GitHub Actions, Docker, Kubernetes, Helm.

The CI/CD in GitHub is not going to change when we move to AWS. We will still use GitHub Actions to build, test, and deploy our applications. The only thing that will change is the deployment target. Instead of deploying to a Kubernetes cluster, we will deploy to AWS.

=====================
Continous Integration
=====================

Continous integration (CI) will be the same, we will build, test, lint or scan our code using GitHub Actions. The only thing that can change is using custom GitHub runners instead of the default GitHub runners, is order to speed up the build process by having all thye dependencies pre-installed on the runner.

Example of CI in GitHub actions for a Python microservice:

.. code-block:: yaml

    name: CI

    on:
      push:
        branches:
          - main
      pull_request:
        branches:
          - main

    jobs:
      build:
        runs-on: ubuntu-latest

        steps:
        - name: Checkout repository
          uses: actions/checkout@v4

        - name: Set up Python 3.12
          uses: actions/setup-python@v5
          with:
            python-version: 3.12

        - name: Install dependencies
          run: |
            python -m pip install --upgrade pip
            pip install -r requirements.txt

        - name: Lint with flake8
          run: |
            flake8 .

        - name: Test with pytest
          run: |
            pytest

        - name: Scan with bandit
          run: |
            bandit -r .

        - name: Scan with safety
          run: |
            safety check --full-report

        - name: Scan with trufflehog
          run: |
            trufflehog --regex --entropy=False .

        - name: Scan with snyk
          run: |
            snyk test

        - name: Scan with sonarcloud
          run: |
            sonar-scanner

        - name: Build Docker image
          run: |
            docker build -t myapp:latest .

        - name: Push Docker image
          run: |
            echo ${{ secrets.DOCKER_PASSWORD }} | docker login -u ${{ secrets.DOCKER_USERNAME }} --password-stdin
            docker push myapp:latest

=========================
Continous deployment (CD)
=========================

+++++++++++++++++++++++++++++++++++
Automated deployment with Terraform
+++++++++++++++++++++++++++++++++++

.. note::

    What is terraform?

    Terraform is an open-source infrastructure as code software tool created by HashiCorp. It enables users to define and provision a datacenter infrastructure using a high-level configuration language known as Hashicorp Configuration Language (HCL).

-------------
Prerequisites
-------------

In order to run terraform we need to install it first. Here is how to install ``terraform`` on Ubuntu:

.. code-block:: bash

    wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
    echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
    sudo apt update && sudo apt install terraform

    # to test it
    terraform --version

We need also to install AWS CLI:

.. code-block:: bash

    sudo apt-get install awscli

    # to test it
    aws --version

------------------------------------
IAM - Identity and Access Management
------------------------------------

Create an account on AWS and configure it:

    - Step 1: Navigate to IAM Dashboard
    
        After signing into the AWS Management Console, open the IAM (Identity and Access Management) service. You can find it by typing "IAM" in the search bar at the top.

    - Step 2: Create a New IAM User

        Click on "Users": On the left sidebar within the IAM dashboard, click on "Users."
        Click on "Create User": You'll see a button or link labeled "Create User." Click on this to start the user creation process.

    - Step 3: User Details

        Enter User Name: Provide a name for the new user. This name should be unique within your AWS account.
        Select AWS Access Type: Choose "Programmatic access" if you want to generate an access key ID and secret access key for using the AWS CLI and SDKs. If you also want the user to be able to log into the AWS Management Console, select "AWS Management Console access" and set a console password.

    - Step 4: Set Permissions

        Attach existing policies directly: This option allows you to attach AWS managed and custom policies directly to the user. Choose the policies that grant the necessary permissions for the user to perform their tasks.
        Add user to group: If you have already created groups with specific policies attached, you can add the user to one of these groups.
        Copy permissions from another user: This option allows you to duplicate the permissions from an existing user to the new user.

    - Step 5: Review and Create

        Review the details of the user, including the name and permissions. If everything looks correct, click on "Create User."

    - Step 6: Security Credentials

        After the user is created, you will be shown the user's security credentials, including the access key ID and secret access key. This is the only time you will be shown the secret access key, so make sure to download it or copy it to a secure location.
        If you've enabled AWS Management Console access, you'll also see the sign-in URL for the user.

    - Step 7: Configure the AWS CLI

        With the new IAM user's access key ID and secret access key, you can now configure the AWS CLI on your local machine:

        Open a terminal or command prompt.
        Run the command ``aws configure``.
        When prompted, enter the new IAM user's access key ID and secret access key. Then, specify your default region name (e.g., europe-central-1) and default output format (e.g., json).

    - Step 8: Test the configuration

        To test the configuration, run the following command:

        .. code-block:: bash

            aws s3 ls

        If the configuration is correct, you should see a list of your S3 buckets.

--------------------------
Writing the terraform code
--------------------------

    Create a new directory for your terraform code and navigate to it:

    .. code-block:: bash

        mkdir aws-ec2-hello-world
        cd aws-ec2-hello-world

    Create a new file named ``index.html`` and add the following code: 

    .. code-block:: html

        <!DOCTYPE html>
        <html>
        <head>
            <title>Hello World</title>
        </head>
        <body>
            <h1>Hello, World!</h1>
            <p>This is my first webpage hosted on AWS EC2.</p>
        </body>
        </html>


    Create a new file named ``main.tf`` and add the following code:

    .. code-block:: bash

        provider "aws" {
        region = "eu-central-1"
        }

        resource "tls_private_key" "access_key" {
        algorithm = "RSA"
        rsa_bits  = 2048
        }

        output "private_key" {
        value     = tls_private_key.access_key.private_key_pem
        sensitive = true
        }

        resource "aws_key_pair" "deployer" {
        key_name   = "ec2-deployer-key"
        public_key = tls_private_key.access_key.public_key_openssh
        }

        resource "aws_security_group" "hello_world_sg" {
        name        = "hello_world_sg"
        description = "Allow SSH and HTTP"

        ingress {
            from_port   = 22
            to_port     = 22
            protocol    = "tcp"
            cidr_blocks = ["0.0.0.0/0"]
        }

        ingress {
            from_port   = 80
            to_port     = 80
            protocol    = "tcp"
            cidr_blocks = ["0.0.0.0/0"]
        }

        egress {
            from_port   = 0
            to_port     = 0
            protocol    = "-1"
            cidr_blocks = ["0.0.0.0/0"]
        }
        }

        resource "aws_instance" "hello_world" {
        ami                    = "ami-03cceb19496c25679"
        instance_type          = "t2.micro"
        key_name               = aws_key_pair.deployer.key_name
        security_groups        = [aws_security_group.hello_world_sg.name]

        user_data = <<-EOF
                    #!/bin/bash
                    sudo yum update -y
                    sudo yum install httpd -y
                    sudo systemctl start httpd.service
                    sudo systemctl enable httpd.service
                    echo "${file("${path.module}/index.html")}" > /var/www/html/index.html
                    EOF

        tags = {
            Name = "HelloWorldInstance"
        }
        }

    Run the code:

    .. code-block:: bash

        terraform init
        terraform plan
        terraform apply
        terraform output -raw private_key > key.pem
        chmod 400 key.pem

        # to destroy the resources
        terraform destroy  

--------------------------------------
Deploying the code with GitHub Actions
--------------------------------------

    1. Create a new repository on GitHub and push the code to it.
    2. Create 2 new secrets in the repository settings: ``AWS_ACCESS_KEY_ID`` and ``AWS_SECRET_ACCESS_KEY``.
    3. Create a new file named ``.github/workflows/deploy.yml`` and add the following code:

    .. code-block:: yaml

        name: Deploy S3 Bucket on index.html Change

        on:
          push:
            paths:
              - 'index.html'

        jobs:
          deploy:
            name: Deploy with Terraform
            runs-on: ubuntu-latest

            steps:
              - name: Checkout Repository
                uses: actions/checkout@v2

              - name: Set up Terraform
                uses: hashicorp/setup-terraform@v1
                with:
                  terraform_version: 1.7.3

              - name: Configure AWS Credentials
                uses: aws-actions/configure-aws-credentials@v1
                with:
                  aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
                  aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
                  aws-region: eu-central-1

              - name: Terraform Init
                run: terraform init

              - name: Terraform Plan
                run: terraform plan

              - name: Terraform Apply
                run: terraform apply -auto-approve
