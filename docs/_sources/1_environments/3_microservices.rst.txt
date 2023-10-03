#################
1.3 Microservices
#################

.. note::

    A microservice is a software architectural style in which a large application is built as a collection of small, independent services. Each service is focused on a specific business capability and communicates with other services through simple, well-defined interfaces. Microservices are designed to be loosely coupled, which means that they can be developed, deployed, and scaled independently of one another.

The main advantage of using microservices is that they allow teams to work on small, manageable pieces of the overall system, rather than one large monolithic codebase. This makes it easier to test, deploy, and scale each service independently, which can lead to faster development times and more reliable systems.

Microservices are typically built using a variety of technologies, and they are often deployed in containers or virtual machines. These services communicate with each other through APIs, which allows them to be written in different languages and run on different platforms.

Microservices also enable teams to use different languages, frameworks, and technologies for different services, making it easier for them to find the best fit for the specific requirement and make the development process more efficient.

In summary, a microservice is a small, independent service that focuses on a specific business capability, and communicates with other services through simple, well-defined interfaces. It is designed to be loosely coupled, which makes it easier to test, deploy, and scale independently, which can lead to faster development times and more reliable systems.

**Monolithic Architecture**
    All processes are tightly coupled and run as a single service. This means that if one process of the application experiences a spike in demand, the entire architecture must be scaled. Adding or improving a monolithic application's features becomes more complex as the code base grows. This complexity limits experimentation and makes it difficult to implement new ideas. Monolithic architectures add risk for application availability because many dependent and tightly coupled processes increase the impact of a single process failure 

**Microservices Architecture**
    With a microservices architecture, an application is built as independent components that run each application process as a service. These services communicate via a well-defined interface using lightweight APIs. Services are built for business capabilities and each service performs a single function. Because they are independently run, each service can be updated, deployed, and scaled to meet the demand for specific functions of an application.

.. image:: ../diagrams/microserviceVSmonolith.png
  :width: 1000
  :alt: microservice VS monolith

The main difference between a monolithic and microservice architecture is how the application is structured and how the different parts of the system interact with each other.

Monolithic architecture is tightly coupled, which means that all the components of the system are closely linked and depend on each other, making it harder to change or update one component without affecting the others. Microservice architecture is loosely coupled, which means that the services are independent of each other and can be updated or changed without impacting the other parts of the system.

Microservices have several advantages over monolithic architecture:
  #. They are easier to scale, as each service can be scaled independently.
  #. They are easier to test, as each service can be tested in isolation.
  #. They are easier to deploy, as each service can be deployed independently.
  #. They are easier to maintain, as each service has a single responsibility and can be updated or changed without impacting the other parts of the system.
