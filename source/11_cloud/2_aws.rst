########################
11.2 Amazon Web Services
########################

.. note::

    Amazon Web Services (AWS) is a collection of remote computing services (also called web services) that together make up a cloud computing platform, offered over the Internet by Amazon.com. The most central and well-known of these services are Amazon EC2 and Amazon S3. The service is advertised as providing a large computing capacity (potentially many servers) much faster and cheaper than building a physical server farm.

.. code-block:: bash

    python3.12 -m venv venv
    . ven/bin/activate
    pip install awscli

===========================================
Hello world: Cloud Agnostic vs Cloud Native
===========================================

++++++++++++++
Cloud Agnostic
++++++++++++++

.. note::

    Cloud agnostic is a term that refers to a software tool or service that is designed to function in any vendor's cloud computing environment. A cloud-agnostic approach to technology can be beneficial to businesses because it allows them to avoid vendor lock-in, which can occur when a company builds internal workflows or adopts third-party tools that are designed to function optimally with a single cloud provider's services.

Step 1: Set Up an AWS Account

    Create an AWS Account: If you don't already have one, go to the AWS website and create an account. You'll need to provide some basic information and a valid credit card.

Step 2: Launch an EC2 Instance

    Sign in to AWS Management Console: Once your account is set up, sign in to the AWS Management Console.

    Launch an EC2 Instance:
    
    - In the AWS Management Console, find and select "EC2" to open the EC2 dashboard.
    - Click on “Launch Instance” to start the process of creating a new virtual server.
    - Select an Amazon Machine Image (AMI), like Amazon Linux 2, which is free tier eligible.
    - Choose an Instance Type (e.g., t2.micro for the free tier) and then click “Next: Configure Instance Details”.
    - Proceed with the default configurations and click “Next” until you reach “Configure Security Group”.
    - Create a new security group and add rules to allow HTTP (port 80) and SSH (port 22) traffic.
    - Review and launch the instance. AWS will prompt you to create and download a key pair. Save this key pair, as it's required to SSH into the server.

Step 3: SSH into Your EC2 Instance

    Connect to Your Instance: Use an SSH client with the key pair file you downloaded to connect to your EC2 instance. The command generally looks like this: ssh -i /path/to/your-key.pem ec2-user@your-instance-public-dns.

Step 4: Install a Web Server

    Update Your Instance: Once connected, update your packages: ``sudo yum update -y``.
    Install a Web Server: Install Apache or Nginx. For Apache: ``sudo yum install httpd -y``.
    Start the Web Server: For Apache: ``sudo systemctl start httpd.service``.
    Configure the Web Server to Start on Boot: ``sudo systemctl enable httpd.service``.

Step 5: Create Your "Hello World" HTML File

    Navigate to the Web Root: For Apache, it's usually /var/www/html.

    Create the HTML File: Use a text editor to create a file named index.html. Here's a simple HTML for a "Hello World" page:

    .. code-block:: html

        <!DOCTYPE html>
        <html>
        <head>
            <title>Hello World</title>
        </head>
        <body>
            <h1>Hello, World!</h1>
            <p>This is my first webpage hosted on AWS.</p>
        </body>
        </html>

    Save the file in the web server's root directory (e.g., /var/www/html).

Step 6: Access Your Website

    Find Your Public DNS/IP: Go back to the EC2 Management Console, select your instance, and find its public DNS or IP address.
    Access in Browser: Enter the public DNS/IP address in a web browser. You should see your "Hello, World!" webpage.

Step 7: Additional Configurations

    You may need to adjust your instance's security group rules in the AWS Management Console to ensure that the HTTP and HTTPS ports (80 and 443) are open to the public.
    For a production environment, you would also need to consider setting up a domain name, SSL/TLS certificates for HTTPS, and possibly a more complex hosting setup like Elastic Beanstalk or AWS Amplify for scalability and ease of deployment.

++++++++++++
Cloud Native
++++++++++++

.. note::

    Cloud native is a term that refers to applications that are container-based, dynamically orchestrated and microservices-oriented. Cloud-native technologies are used to develop applications built with services packaged in containers, deployed as microservices and managed on elastic infrastructure through agile DevOps processes and continuous delivery workflows.


Step 1: Create Your HTML File

    irst, write the HTML for your "Hello World" page. You can use a text editor like Notepad or VS Code for this. Here's a basic example:


    .. code-block:: html

        <!DOCTYPE html>
        <html>
        <head>
            <title>Hello World</title>
        </head>
        <body>
            <h1>Hello, World!</h1>
            <p>This is my first webpage hosted on AWS S3.</p>
        </body>
        </html>

    Save this file as index.html.

Step 2: Set Up an AWS Account

    If you don't have an AWS account, go to the AWS website and sign up. You'll need to provide some basic information and a valid credit card.

Step 3: Create an S3 Bucket

    Log in to the AWS Management Console and navigate to the S3 service.
    Create a new bucket:
    Click on "Create bucket".
    Give your bucket a unique name, which will be part of your website URL (e.g., my-hello-world-website).
    Select a region.
    Uncheck “Block all public access” to make the website publicly accessible. Acknowledge the warning that the bucket will be public.
    Click on "Create bucket".

Step 4: Upload Your HTML File

    Open your newly created bucket and click on "Upload".
    Upload your index.html file.

Step 5: Enable Static Website Hosting

    In your bucket, go to the “Properties” tab.
    Scroll down to “Static website hosting”.
    Select “Use this bucket to host a website”.
    Set index.html as both the Index document and the Error document.
    Click “Save”.

Step 6: Set Bucket Permissions

    Go to the “Permissions” tab of your bucket.

Edit the bucket policy to make the content publicly readable. You can use the following policy, replacing YOUR_BUCKET_NAME with the actual name of your bucket:

    .. code-block:: json

        {
            "Version": "2012-10-17",
            "Statement": [
                {
                    "Sid": "PublicReadGetObject",
                    "Effect": "Allow",
                    "Principal": "*",
                    "Action": "s3:GetObject",
                    "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
                }
            ]
        }

    Click “Save”.

Step 7: Access Your Website

    Find the endpoint URL: Go back to the bucket's “Properties” tab and look under “Static website hosting” for the Endpoint URL.
    Open the URL in a web browser. You should see your "Hello, World!" webpage.

Step 8: DNS Alias


    To create a DNS alias for your S3-hosted website, you'll typically use Amazon Route 53, a scalable and highly available Domain Name System (DNS) web service. This process involves purchasing a domain name (if you don't have one already) and then creating a DNS alias that points to your S3 bucket. Here's how to do it:

    Register a Domain (if you don't have one)

        Go to the AWS Management Console and open the Route 53 console.
        In Route 53, go to “Registered domains” and click “Register domain”.
        Follow the instructions to choose a domain name and complete the registration process. Note that this will incur a yearly registration fee.

    Create a Hosted Zone

        In the Route 53 console, go to “Hosted zones”.
        Click “Create hosted zone”.
        Enter your domain name in the “Domain Name” field.
        Choose “Public Hosted Zone”.
        Click “Create”.

    Set Up a DNS Alias for Your S3 Bucket

        In your hosted zone, click “Create Record”.
        In the “Record name” field, enter the desired subdomain (e.g., www for www.example.com).
        In the “Record type” field, select “A - IPv4 address”.
        Enable the “Alias” toggle.
        In the “Alias target” field, select your S3 bucket endpoint from the dropdown list. It should appear under “Alias to S3 website endpoint”.
        Click “Create records”.

    Configure Your S3 Bucket to Use the Custom Domain

        Go back to the S3 console and open your bucket.
        Rename your bucket to match the full domain name (e.g., www.example.com). Note: The bucket name must exactly match the domain or subdomain.
        Follow the previously mentioned steps to enable static website hosting for your bucket and set the correct permissions.

