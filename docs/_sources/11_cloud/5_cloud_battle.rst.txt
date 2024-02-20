#################
11.5 Cloud battle
#################

==============
Financial data
==============

============================  ========================  =============================================  ========================
                              Amazon AWS                Microsoft Azure* (include all cloud services)  Google Cloud
============================  ========================  =============================================  ========================
Founded                       March 2006(17 years ago)  October 2008(15 years ago)                     April 2008(15 years ago)
Market share(Q4 2023)         **32%**                   24%                                            11%
Revenue (Q4 2023)             $24.2 billion             $25.9 billion                                  $9.2 billion
Revenue (2023)                $90.8 billion             $96.8 billion                                  $33.7 billion
Sales growth(2023)            13%                       19%                                            26%
Operating income(2023)        $7.2 billion              $12.5 billion                                  **$864 milion**
Parent company revenue(2023)  **$170 billion**          $62 billion                                    $86 billion
============================  ========================  =============================================  ========================

From: https://www.crn.com/news/cloud/2024/aws-vs-microsoft-vs-google-cloud-earnings-q4-2023-face-off

* Microsoft Azure includes all cloud services, including Azure, Microsoft 365, Dynamics 365, and LinkedIn under the "Intelligent Cloud" segment.

==============
Cloud services
==============

====================  ===================  ==============================================  ==============================
                      Amazon AWS           Microsoft Azure* (include all cloud services)   Google Cloud
====================  ===================  ==============================================  ==============================
Compute               Amazon EC2           Azure Virtual Machines                          Google Compute Engine
Serverless            AWS Lambda           Azure Functions                                 Google Cloud Functions
Storage               Amazon S3            Azure Blob Storage                              Google Cloud Storage
Database(RDBMS)       Amazon RDS           Azure SQL Database                              Google Cloud SQL
Database(NoSQL)       Amazon DynamoDB      Azure Cosmos DB                                 Google Cloud Bigtable
Networking            Amazon VPC           Azure Virtual Network                           Google Virtual Private Cloud
Kubernetes            Amazon EKS           Azure Kubernetes Service                        Google Kubernetes Engine
Machine Learning      Amazon SageMaker     Azure Machine Learning                          Google AI Platform
CI/CD                 AWS CodePipeline     Azure DevOps                                    Google Cloud Build
Monitoring            Amazon CloudWatch    Azure Monitor                                   Google Cloud Monitoring
Identity              AWS IAM              Azure Active Directory(Entra ID)                Google Cloud Identity
Domain Name System    Amazon Route 53      Azure DNS                                       Google Cloud DNS
====================  ===================  ==============================================  ==============================

=====================
DevOps Implementation
=====================

================================  =================================================================================================================  =================================================================================================  =================================================================================================
Feature                           AWS                                                                                                                Azure                                                                                                 GCP                                                                                                  |
================================  =================================================================================================================  =================================================================================================  =================================================================================================
**CI/CD Tools**                   AWS CodePipeline for CI/CD. AWS CodeBuild for build services.                                                      Azure Pipelines for CI/CD, integrates with GitHub Actions.                                            Cloud Build for CI/CD, integration with popular tools like GitHub, GitLab.                          |
**Source Control**                AWS CodeCommit, a managed source control service.                                                                  Azure Repos provides Git repositories for source control.                                             Cloud Source Repositories, fully-featured, scalable, private Git repositories.                      |
**Monitoring**                    Amazon CloudWatch for monitoring and observability.                                                                Azure Monitor for full-stack monitoring.                                                              Google Operations (formerly Stackdriver) for monitoring, logging, and diagnostics.                   |
**Logging**                       AWS CloudTrail for tracking user activity and API usage.                                                           Azure Log Analytics for log-based data querying and analysis.                                         Cloud Logging for storing, searching, analyzing, monitoring, and alerting on log data.              |
**Configuration Management**      AWS Systems Manager for viewing and controlling infrastructure.                                                    Azure Automation for automating tasks and configuration management.                                   Cloud Deployment Manager for resource management and configuration.                                  |
**Infrastructure as Code (IaC)**  AWS CloudFormation for creating and managing resources with templates.                                             Azure Resource Manager (ARM) templates for declarative resource deployment.                           Google Cloud Deployment Manager for infrastructure management through code.                          |
**Serverless Computing**          AWS Lambda for running code without provisioning servers.                                                          Azure Functions for event-driven programming.                                                         Cloud Functions for event-driven serverless applications.                                            |
**Container Management**          Amazon Elastic Kubernetes Service (EKS) for Kubernetes management. Amazon ECS for container orchestration.         Azure Kubernetes Service (AKS) for Kubernetes.Azure Container Instances for container deployment.     Google Kubernetes Engine (GKE) for Kubernetes management, Cloud Run for stateless containers.        |
**Security & Compliance**         AWS Identity and Access Management (IAM) for fine-grained access control.Comprehensive compliance certifications.  Azure Security Center for unified security management. Extensive compliance offerings.                Cloud Identity & Access Management (IAM) for resource access control. Strong security features.      |
**Developer Tools**               Broad set of tools including AWS CLI, SDKs, and IDE integrations.                                                  Visual Studio integration, Azure CLI, SDKs.                                                           Cloud SDK, command-line tools, and IDE plugins.                                                      |
================================  =================================================================================================================  =================================================================================================  =================================================================================================

++++++++
Analysis
++++++++

- **CI/CD Tools**: All three providers offer robust CI/CD tools designed to automate the software release process. AWS CodePipeline and Azure Pipelines both support complex workflows, while GCP's Cloud Build provides flexibility and integration with third-party options.
- **Monitoring and Logging**: AWS CloudWatch and CloudTrail offer comprehensive monitoring and logging, Azure's solutions integrate deeply with its ecosystem for a unified monitoring experience, and GCP's Operations suite provides advanced logging and monitoring features with cross-platform support.
- **Infrastructure as Code (IaC)**: AWS CloudFormation, Azure Resource Manager templates, and GCP's Deployment Manager each provide a powerful way to manage infrastructure using code, enabling DevOps teams to automate and replicate environments easily.
- **Serverless and Containers**: Serverless computing and container management are well-supported across all platforms, with each offering their managed Kubernetes services (EKS, AKS, GKE) and serverless solutions (Lambda, Functions, Cloud Functions) that cater to different application architectures and scaling needs.
- **Security and Compliance**: AWS, Azure, and GCP prioritize security and compliance, offering tools and features to help maintain a secure and compliant cloud environment. Their services include identity and access management, threat detection, and a wide range of compliance certifications.

==========
Conclusion
==========

.. note:: 
    
    AWS, Azure, and GCP each provide a comprehensive suite of cloud services and DevOps tools, catering to a wide range of use cases and application architectures.
    
    The choice of cloud provider depends on specific requirements, such as existing infrastructure, application needs, and organizational preferences.