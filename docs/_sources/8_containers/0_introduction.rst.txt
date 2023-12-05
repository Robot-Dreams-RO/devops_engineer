################
8.0 Introduction
################

.. note::

    Docker is a platform that allows developers to easily create, deploy, and run applications in containers. 
    Containers are lightweight, portable, and self-sufficient packaging of an application and its dependencies. They provide a consistent runtime environment and are isolated from the host operating system.

Docker is an open-source platform that provides a set of tools for creating, deploying, and managing containers. It includes a container engine, which is responsible for creating and running containers, and a set of command-line tools for interacting with the engine. Docker also provides a centralized hub, called the Docker Hub, where developers can share and discover container images.

Containers are similar to virtual machines, but they are more lightweight and efficient. Unlike virtual machines, which require a separate operating system for each instance, containers share the host operating system kernel, which makes them more efficient in terms of resources. Containers also provide a consistent runtime environment, regardless of the host environment, which makes them more portable and easier to deploy.

Docker allows developers to package an application and its dependencies into a single container, which can be easily deployed and run on any host that supports Docker. This makes it easier to develop and test applications locally, and then deploy them to production with confidence.

Docker also provides a set of orchestration tools, such as Docker Compose and Docker Swarm, which allow developers to easily manage and scale multiple containers.

In summary, Docker is a platform that allows developers to easily create, deploy, and run applications in containers. Containers are lightweight, portable, and self-sufficient packaging of an application and its dependencies, which provide a consistent runtime environment and are isolated from the host operating system. Docker provides a set of tools for creating, deploying, and managing containers, and a centralized hub for sharing and discovering container images. It also provides a set of orchestration tools for managing and scaling multiple containers.

An approach to software development known as containerization involves packaging an application or service along with its dependencies and settings into a single file known as a container image. The containerized application can be tested individually and installed on the host operating system as a container image instance (OS).

**Why do we need containers?**

To avoid *"it works on my machine"*. By having a template from which we can create an image that can be instantiated into a container we are avoiding all the inconsistencies around the different environments: different software versions, hardware, users, and directory structure.

Software containers function as a common unit of software deployment that can include many types of code and dependencies, just like shipping containers enable items to be carried by ship, rail, or truck regardless of the contents within. Developers and Operation Engineers can deploy software across environments with little to no modification by containerizing it in this way.

=====================
What is a container?
=====================

Containers are software packages that come with everything needed to execute in any environment. Containers virtualize the operating system in this manner, enabling them to run anywhere, including on a developer's own laptop as well as on a public cloud or a private data center.

Simply put, a container is a sandboxed process on your machine that is isolated from all other processes on the host machine

==================
Containers vs Pods
==================

The smallest deployable compute units that Kubernetes allows you to generate and control are called pods.

A **collection of one or more containers**, with common storage and network resources, and a specification for how to execute the containers, is referred to as a **"pod"** (as in a pod of whales or pea pod).
The components of a pod are always co-located, co-scheduled, and executed in a common context. A pod includes one or more tightly connected application containers and serves as a representation of an application-specific "logical host". Applications running on the same physical or virtual system are comparable to cloud applications running on the same logical host in non-cloud scenarios.

===============
What is Docker?
===============

Docker is an open-source project for automating the deployment of apps as portable, autonomous containers that can run on the dev's machine, company's data center or cloud.

A Docker container is:
- is a runnable instance of an image. You can create, start, stop, move, or delete a container using the DockerAPI or CLI.
- can be run on local machines, virtual machines or deployed to the cloud.
- is portable (can be run on any OS)
- containers are isolated from each other and run their own software, binaries, and configurations.

What is a container image?

When running a container, it uses an isolated filesystem. This custom filesystem is provided by a container image. Since the image contains the container's filesystem, it must contain everything needed to run an application - all dependencies, configuration, scripts, binaries, etc. The image also contains other configuration for the container, such as environment variables, a default command to run, and other metadata.

===============
What is Podman?
===============

Podman is a daemon less container engine for developing, managing, and running containers.

Read more in https://fedoramagazine.org/docker-and-fedora-37-migrating-to-podman/