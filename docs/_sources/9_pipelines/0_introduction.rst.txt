###############
0. Introduction
###############

.. image:: ../diagrams/devops.png
  :alt: A diagram showing schematically how a Continuous Integration and Continuous Deployment works
  :width: 1000 px

CI/CD (Continuous Integration/Continuous Deployment) pipelines are a set of automated processes that are used to build, test, and deploy software changes
Think of it as a workflow or assembly line for your software, where each step performs a specific function, ensuring that code is built, tested, and deployed reliably and efficiently.
The goal of these pipelines is to automate the software delivery process and to ensure that changes are delivered to production quickly and safely.
These are crucial practices in modern software development that focus on automating and streamlining the process of building, testing, deploying and releasing software.

======================
Continuous Integration
======================

CI (Continuous Integration) is the practice of frequently integrating code changes into a shared repository, such as Git, multiple times a day. Each integration triggers an automated build and a series of tests to ensure that the newly added code does not break existing functionality. Key components of CI include:

#. **Automated Builds**: Code changes are automatically compiled or built into executable software.
#. **Automated Testing**: A suite of automated tests, including unit tests and integration tests, is run to identify any defects or issues introduced by the code changes.
#. **Frequent Integration**: Developers frequently merge their code changes into the shared repository, promoting collaboration and reducing integration issues.

.. note::
    The primary goals of CI are to catch and fix integration issues early in the development process, improve code quality, and ensure that software remains in a working state at all times.

The notion of Continuous Integration began to gain prominence in the early 2000s, with notable contributions from Martin Fowler and Kent Beck, among others. Grady Booch, the software engineer behind the Unified Modeling Language (UML), initially proposed this term in 1991 within the Booch method, a precursor to UML. However, it's worth noting that Booch's proposal did not advocate integrating code multiple times a day. It wasn't until 1997 when Kent Beck and Ron Jeffries introduced Extreme Programming (XP) that the concept of CI took a more frequent integration approach, promoting the integration of code changes multiple times a day, possibly even dozens of times.

Early adopters of these principles recognized the advantages of regularly incorporating code changes into the shared codebase. This practice was instrumental in swiftly detecting and addressing integration issues as they surfaced, thereby preventing the often chaotic situations referred to as "integration hell." This term describes the challenging scenarios that arose when developers postponed integrating their work for extended periods.

The evolution of Continuous Integration was further facilitated by the emergence of CI tools such as CruiseControl in 2001 and Jenkins (originally known as Hudson) in 2005. These tools played a pivotal role in automating the CI process, simplifying the implementation of CI practices for development teams.

=====================
Continuous Deployment
=====================

CD (Continuous Deployment) is the process of automatically deploying code changes to production as soon as they pass all of the necessary tests and quality checks. 

Continuous Deployment is an extension of CI that automates the deployment of code changes to production environments after they pass all necessary tests. While the term "Continuous Deployment" implies automatic deployment to production, there's also a similar practice known as "Continuous Delivery" that involves automated deployment to staging or pre-production environments, with a manual approval step before deploying to production.

This allows organizations to deliver changes to customers faster and with less risk.

Key aspects of CD include:

#. **Automated Deployment**: Once code changes pass all tests, they are automatically deployed to the target environment. In Continuous Deployment, this includes production.
#. **Testing in Production-like Environments**: Code changes are tested in environments that closely mimic the production environment, ensuring that they will work as expected when deployed.
#. **Rollback Procedures**: CD pipelines often include automated rollback procedures in case any issues are detected after deployment.

.. note::
    The primary goal of CD is to deliver code changes to end-users as quickly and reliably as possible, reducing manual intervention and the risk of human error in the deployment process.


.. image:: ../diagrams/pipeline.png
  :alt: A diagram showing schematically how a pipeline works
  :width: 1000 px


A typical CI/CD pipeline includes the following stages:

#. **Source Control:** The pipeline usually starts with code residing in a version control system (e.g., Git). Developers commit their code changes to this repository.
#. **Build:** In this step, the code is compiled, and necessary dependencies are fetched. The output is typically an executable, library, or deployable artifact.
#. **Testing:** Automated tests are run on the code. This includes unit tests (testing individual components), integration tests (testing interactions between components), and possibly other forms of testing like load testing, security testing, and user acceptance testing.
#. **Artifact Storage:** The resulting build artifacts are stored in a secure location. These artifacts are often versioned, making it easy to roll back to previous versions if needed.
#. **Deployment:** Once the code has passed all tests, it's deployed to a staging environment. This environment closely resembles the production environment but is separate, allowing further testing without affecting users.
#. **Approval (Optional):** In some cases, there's an approval step where stakeholders can review the changes in the staging environment and give their go-ahead for deployment to production.
#. **Release to Production:** If the code performs well in the staging environment and is approved, it's released into the production environment, making it available to end-users.
#. **Monitoring:** After deployment, the pipeline often includes continuous monitoring of the production environment to ensure that the new code is performing well and to detect and respond to any issues promptly.

Throughout this process, if any step fails (e.g., a test doesn't pass, a security vulnerability is detected), the pipeline can be configured to halt and alert developers, preventing potentially problematic code from reaching production.

CI/CD pipelines can be integrated with a variety of tools, such as ``Azure Pipelines``, ``Jenkins``, and ``GitLab CI/CD``, to automate the different stages of the pipeline, and can also be integrated with cloud platforms like AWS, Azure, and GCP.

=================
Benefits of CI/CD
=================

CI/CD pipelines are a key tool for organizations that want to deliver software changes quickly and safely, and they can help organizations to improve the quality and reliability of their software while also reducing the time and cost of software delivery.

Key benefits of using CI/CD pipelines include:

#. **Automation:** Reducing manual intervention and human error. Automation minimizes manual tasks, reducing the chance of errors and freeing up developer time for more valuable work.
#. **Speed:** Accelerating the software development lifecycle. Code changes are integrated and deployed more frequently, speeding up the development and release process.
#. **Consistency:** Ensuring that each code change undergoes the same rigorous process. Automated testing ensures that code changes meet quality standards and do not introduce regressions.
#. **Quality:** Catching and addressing issues early in development, making them easier and cheaper to fix.
#. **Risk Reduction:** Providing a safety net for deployments. CI/CD promotes a consistent and repeatable process for building, testing, and deploying software.
#. **Collaboration:** Promoting collaboration between developers, testers, and other stakeholders. CI/CD encourages developers to integrate their code changes frequently, reducing integration issues and promoting collaboration.
#. **Visibility:** Providing visibility into the software delivery process. CI/CD pipelines provide a clear view of the status of code changes as they move through the pipeline, making it easy to identify bottlenecks and issues.
