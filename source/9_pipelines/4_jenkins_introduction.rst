###########################
9.4 Introduction to Jenkins
###########################

.. image:: ../diagrams/jenkins_logo.png
  :alt: Jenkins logo

================
What is Jenkins?
================

.. note::

    Jenkins is an open-source automation server widely used for building, testing, and deploying software. It is one of the most popular tools in the field of continuous integration and continuous deployment (CI/CD). It provides a way to automate the software development process, including building, testing, and deploying code, enabling developers to focus on writing code.

It was initially developed as an open-source project under the name "Hudson" and in 2011 was renamed to Jenkins after a dispute with Oracle. Jenkins is written in Java and is designed to be highly configurable, making it a versatile tool for automating a wide range of tasks.

The full Jenkins documentation can be found `here <https://www.jenkins.io/doc/book/>`_ .

========================================
Flexibility and integration capabilities
========================================

It is a highly adaptable automation server that addresses a wide range of development languages, platforms and tools.

Jenkins is not tied to any specific development language or platform. It supports an extensive array of programming languages, including but not limited to Java, Python, JavaScript, Ruby, C++, and more. This makes it suitable for a diverse set of projects, from web applications to mobile apps to embedded systems. Jenkins flexibility allows development teams to use the tools and technologies they are most comfortable with.

One of Jenkins standout features is its plugin ecosystem. With over 2000 plugins available, Jenkins can be extended and customized to accommodate virtually any development or deployment need. For example, Jenkins can be enhanced with plugins for Git, Docker, Kubernetes, Jenkins Pipeline DSL, and cloud platforms like AWS, Azure, and Google Cloud. This extensibility ensures that Jenkins can adapt to the specific requirements of different projects and organizations.

At https://stats.jenkins.io/ you will find various statistics related to Jenkins such as:

- List of plugins
- Top plugins
- Plugin Installation Trend
- Jenkins plugin dependency graph

==================
Deployment Options
==================

Jenkins offers flexibility in terms of deployment. It can be set up on-premises within an organization's data center or run in the cloud on infrastructure-as-a-service (IaaS) or platform-as-a-service (PaaS) platforms. Running Jenkins in the cloud can also provide scalability and high availability benefits.

Jenkins is distributed as WAR files, native packages, installers, and Docker images. The full list of Jenkins installation options can be found here: https://www.jenkins.io/download/.

Jenkins can be deployed in:

- Docker
- Kubernetes
- Debian/Ubuntu
- Fedora
- Red Hat/Alma/Rocky
- macOS
- Windows
- FreeBSD

It can be easily integrated with a plethora of development and DevOps tools and services, including:

#. **Version Control Systems (VCS)**: Jenkins integrates smoothly with popular VCS systems like Git, Subversion, and Mercurial. This integration enables automatic build triggering and version control operations.
#. **Containerization with Docker**: Jenkins can orchestrate Docker containers, allowing users to build, deploy, and manage containerized applications. Jenkins pipelines can include Docker commands for tasks like building Docker images and pushing them to container registries.
#. **Container Orchestration with Kubernetes**: Jenkins can interact with Kubernetes clusters to deploy and manage containerized applications. This is extremely useful for microservices architectures.
#. **Configuration Management Tools**: Jenkins can be used in conjunction with configuration management tools like Ansible, Puppet, and Chef to automate infrastructure provisioning and configuration.
#. **Test Automation Frameworks**: Jenkins seamlessly integrates with various testing frameworks, including JUnit, Selenium, and others, enabling automated testing as part of the CI/CD pipeline.
#. **Collaboration and Communication Tools**: Jenkins can notify development teams of build and deployment status using communication tools like Slack, email, or custom webhooks.
#. **Artifact Repositories**: Jenkins can publish and retrieve artifacts from artifact repositories such as Nexus and Artifactory, ensuring that build artifacts are versioned and easily accessible.

Jenkins broad language and platform support, extensibility through plugins, deployment flexibility, and seamless integration capabilities make it a top candidate for automating software development and deployment workflows. It empowers organizations to adapt to their specific technology stack and development practices while integrating with the tools and services they rely on to build, test, and deliver high-quality software.


======================
Jenkins release cycles
======================

The Jenkins project operates on two release cycles: **Stable (LTS)** and **Regular (Weekly)**.

1. **Stable (LTS)**: Long-Term Support (LTS) release baselines are selected every 12 weeks from the continuous stream of regular releases. Every 4 weeks, a new stable release is published incorporating backports for bug fixes and security updates.

2. **Regular releases (Weekly)**: This release cycle quickly provides users and plugin developers with bug fixes and new features. It is generally delivered on a weekly basis.


