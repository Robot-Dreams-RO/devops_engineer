############
12.0 Project 
############

=============================================================
Build and deploy a chatbot in the cloud or 'bot in the cloud'
=============================================================

===============
Project purpose
===============

.. note::

    This project is optional!

If you choose to do this project you will supplement the theoretical knowledge gained during the course with practical experience that will help you a lot in understanding how and when you can apply the knowledge learned in this course.

=====================
Project prerequisites
=====================

The project is broken down in mini sub chapter tasks, that at the end will give you an insight of what we're doing everyday.

The DevOps work is focused on helping everybody else to be more productive. This course is focused on making you a complete developer.

====================
Project requirements
====================

.. note::
    
    You need to build a traditional conversational bot using Python and OpenAI.

Building a chatbot with `OpenAI` involves several steps, such as setting up the environment, creating the necessary files, training the bot, interacting with it, etc.

Documentation of how to connect with OpenAI can be found here: https://platform.openai.com/docs/api-reference

Before we can learn how to build a bot, we need to understand how to run a Linux server, automate installation of prerequisites of programming language, write the code itself, build, test, package, deploy, in Linux, Docker, Kubernetes and Cloud.

So we will split this project into two phases:

- Phase 1: Environment setup and bot building
- Phase 2: Cloud deployment automation

After each phase there will be a session where those who choose to do this project will present their progress so far and receive feedback to improve their skills.

=========
Deadlines
=========

Phase 1 will start after course 1 and end after course 13. So in course 14 you need to show your progress.

Phase 2 will start after course 15 and end after course 23. So in course 24 (the last course) you need to show your progress.

====================
Phase 1 requirements
====================

1. After course 1 - 2:

    - Configuring a Linux machine with Python version 12 and libraries. Use Fedora or Ubuntu machine: ``docker run -it ubuntu:latest bash`` or ``docker run -it fedora:latest bash``

1. After course 3:

    - Write a bash / Makefile script that automatically installs the project dependencies on the Linux Machine.

1. After course 4 - 6:

    - Build the chatbot using ``OpenAI`` - that answers to questions using the ``/message`` endpoint 
    - Build the ``/healthcheck`` endpoint - that returns the health of the chatbot
    - Build the ``/version`` endpoint - that returns the version of the chatbot stored in a VERSION file on repository

1. After course 7 - 8:

    - Finish writing the necessary unit tests

1. After course 12:

    - CI pipeline to be completed: pylint, mypy, pytest, coverage.

1. After course 13:

    - Finalize the documentation writing

====================
Phase 2 requirements
====================

1. After course 16:

    - Deploy the chatbot inside a Docker container
    - Run the chatbot using Docker

1. After course 18:

    - Write a Helm Chart for your chatbot to deploy it on Kubernetes.

1. After course 20:

    - Run the Terraform to deploy the chatbot in the cloud.

1. After course 22:

    - Configure the CD pipeline that automatically deploys the application to the cloud if all unit tests are passed
