########
0.5 TODO
########

=========
Questions
=========

1. What is a KPI for DevOps?

    a. Meantime to failure recovery
    b. Deployment frequency
    c. All of them
    d. Percentage of failed deployments
    e. Number of failed HTTP connections


2. What is not an Agile Ceremony?

	a. Retrospective
	b. Release
	c. Review
	d. Refinement

3. What are the continuous integration steps?

	a. build, test, release
	b. debug, deploy, deliver
	c. compile, release, deploy
	d. build, release, deploy

4. What is not a DevOps tool?

	a. Jenkins
	b. Tensorflow
	c. Kubernetes
	d. Ansible

5. What is a DevOps principle?

	a. All of them
	b. Automate everything
	c. Measure everything
	d. Fail fast
	e. Continuous improvement

6. What is a DevOps practice?

	a. Continuous integration
	b. Continuous delivery
	c. All of them
	d. Continuous deployment
	e. Continuous monitoring

7. What is not a DevOps culture?

	a. Collaboration
	b. Transparency
	c. Accountability
	d. Trust

8. What is an Agile Manifesto principle?

	a. Individuals and interactions over processes and tools
	b. Working software over comprehensive documentation
	c. Customer collaboration over contract negotiation
	d. Responding to change by following a plan
	e. All of them.

9. What is a SCRUM artefact?

	a. Sprint
	b. Product backlog
	c. All of them
	d. Sprint backlog
	e. Sprint planning

10. What is Software Development Life Cycle?

	a. Planning, analysis, design, implementation, testing, deployment, maintenance
	b. Planning, analysis, design, implementation, testing, deployment
	c. Planning, analysis, design, implementation, testing
	d. Planning, analysis, design, implementation

11. What is SRE?

	a. Site Reliability Engineering
	b. Software Reliability Engineering
	c. System Reliability Engineering
	d. Scalable Reliability Engineering

12. What is a sprint in Agile?

	a. A sprint is a short, time-boxed period when a scrum team works to complete a set amount of work.
	b. A sprint is a long, time-boxed period when a scrum team works to complete a set amount of work.
	c. A sprint is a short, time-boxed period when a scrum team works to complete the least amount of work.
	d. A sprint is a long, time-boxed period when a scrum team works to complete the most amount of work.

13. The Product Backlog is ordered by?

	a. The Product Owner with the most valuable items placed at the top.
	b. Risk, where safer items are at the top, and riskier items are at the bottom.
	c. Items are randomly arranged.
	d. Size, where small items are at the top and large items are at the bottom.

14. What does it mean for a Development Team to be cross-functional?

	a. The Development Team includes not only developers but also business analysts, architects, and testers.
	b. The Development Team includes cross-skilled individuals who are able to contribute to do what is necessary to deliver an increment of software.
	c. Developers on the Development Team work closely with business analysts, architects, developers and testers who are not on the team.
	d. The Development Team is a virtual team drawing from separate teams of business analysts, architects, developers and testers.

15. Who determines how work is performed during the Sprint? (Choose the best answer.)

	a. Architects.
	b. The Development Team.
	c. The Scrum Master.
	d. Subject matter experts.
	e. Development Team managers.

16. True or False: When multiple teams work together on the same product, each team should maintain a separate Product Backlog.

	a. True
	b. False

17. Which of the following best describes an increment of working software?

	a. A decomposition of all Product Backlog items into tasks for future Sprint Backlog lists.
	b. Additional features in a usable state that complement those delivered in previous iterations.
	c. A new user interface design for functionality delivered in previous iterations.
	d. An automated test suite to verify functionality delivered in previous iterations.
	e. UML diagrams that describe how to deliver functionality in future iterations.

=======
Answers
=======

1.
**Answer:** c. None. All of them are important to DevOps

**Explanation:**

	- Meantime to failure recovery(Average time taken to recover from a failure) is default metric used all over software world, and it mesure time to recover from failure. 
	- Deployment frequency(The frequency in which the deployment occurs) is how often deployment occurs, it's rarely used metric but it's used in combination with failed deployments to calculate Percentage of failed deployments.
	- Percentage of failed deployments is the number of times the deployment fails. 
	- Number of failed HTTP connections it's a metric used to measure availability of the application.

2.
**Answer:** b. Release

**Explanation:**

	- Retrospective is the ceremony where the team reflects on the past sprint and discusses what went well, what could be improved, and what they will commit to improve in the next sprint.
	- Review is the ceremony where the team demonstrates the work they have completed in the sprint to the Product Owner and other stakeholders.
	- Refinement is the ceremony where the team discusses the upcoming work in the backlog and prepares it for the next sprint.
	- Release is not a ceremony, it's a process of releasing the software to the customer.

3.
**Answer:** a. build, test, release

**Explanation:**

	- Build, test, release are the continuous integration steps where we take the code compile it/package it, run the tests and release it to the repository.
	- Debug, deploy, deliver are not the continuous integration steps.
	- Compile, release, deploy are not the continuous integration steps.
	- Build, release, deploy are not the continuous integration steps.

4.
**Answer:** b. Tensorflow

**Explanation:**
	- Jenkins is a continuous integration tool.
	- Kubernetes is a container orchestration tool.
	- Ansible is a configuration management tool.
	- Tensorflow is a machine learning library

5.
**Answer:** a. All of them are DevOps principles

**Explanation:** By automation, monitoring,failing fast and continuous improvement we can deliver faster, better and more reliable software.

6.
**Answer:** c. All of them are DevOps principles

**Explanation:** 

	- Continous integration means that our code is being automaticaly packaged and tested on every commit.
	- Continous delivery means that our code is being automaticaly packaged and tested on every commit and it's ready to be deployed to production.
	- Continous deployment means that our code is being automaticaly packaged and tested on every commit and it's automaticaly deployed to production.
	- Continous monitoring means that we are monitoring our application and infrastructure to become proactive and prevent failures or reactive by having enough information to fix the problem fast.

7.
**Answer:** c. Accountability

**Explanation:** Collaboration, transparency, trust are all DevOps culture principles, accountability is part of corporate culture

8.
**Answer:**  e. All of them are Agile Manifesto principles

**Explanation:** `Agile Manifesto <https://agilemanifesto.org/>`_ 

9.
**Answer:** c. All of them

**Explanation:** Sprint, Sprint backlog, Product backlog, and Sprint planning are all part of SCRUM. 

10.
**Answer:** a. Planning, analysis, design, implementation, testing, deployment, maintenance

**Explanation:** Life cycle of software development is a process of planning, analysis, design, implementation, testing, deployment, maintenance.

11.
**Answer:** a. Site Reliability Engineering

**Explanation:** Site Reliability Engineering is a discipline that incorporates aspects of software engineering and applies them to infrastructure and operations problems.

12.
**Answer:** a. A sprint is a short, time-boxed period when a scrum team works to complete a set amount of work.

**Explanation:** Size of one sprint is 1-4 weeks, it's time-boxed, and the team works to complete a set amount of work which is decided before the sprint starts.

13.
**Answer:** a. The Product Owner with the most valuable items placed at the top.

**Explanation:** Product Owner is responsible for ordering the Product Backlog, and the most valuable items are placed at the top.

14.
**Answer:**

b. The Development Team includes cross-skilled individuals who are able to contribute to do what is necessary to deliver an increment of software.
d. The Development Team is a virtual team drawing from separate teams of business analysts, architects, developers and testers.

**Explanation:** In agile Development team in composed of developers and product owner, and they are cross-functional, meaning that they have all the skills necessary to deliver an increment of software.

15.
**Answer:** b. The Development Team.

**Explanation:** Development team is self-organizing, meaning that they decide how to do the work.

16.
**Answer:** b. False

**Explanation:** When multiple teams work together on the same product, they should maintain a single Product Backlog.

17.
**Answer:** b. Additional features in a usable state that complement those delivered in previous iterations.

**Explanation:** Increment of working software is a new functionality that is delivered in a usable state and it complements the functionality delivered in previous iterations.

=============================
Write your first Hello World!
=============================

Open `Python interpreter <https://replit.com/languages/python3>`_ 

.. code-block:: python

    print('Hello, world!')
    print('My name is XXX')

Open `Bash interpreter <https://replit.com/languages/bash>`_ 

.. code-block:: bash

    echo "Hello World"
    echo "My name is XXX"

Open `Go interpreter <https://replit.com/languages/go>`_ 

.. code-block::

    package main
    import "fmt"
    func main() {
        fmt.Println("Hello, world!")
        fmt.Println("My name is XXX")
    }
