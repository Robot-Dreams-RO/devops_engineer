##########
9.4 ArgoCD
##########

.. note::

    Argo CD is a GitOps-based continuous delivery platform for Kubernetes applications. It provides a way to declaratively manage applications deployed in a Kubernetes cluster, using Git as the source of truth for application definitions and configurations.

Application definitions, configurations, and environments should be declarative and version controlled. Application deployment and lifecycle management should be automated, auditable, and easy to understand.

Argo CD continuously monitors the state of the deployed applications and automatically syncs them with the desired state defined in Git. If a drift is detected between the deployed application and the desired state, Argo CD will automatically reconcile the drift to bring the application back to the desired state.

Some key features of Argo CD include:

    #. **GitOps**: Using Git as the source of truth for application definitions and configurations.
    #. **Continuous Deployment**: Automatically syncing deployed applications with the desired state defined in Git.
    #. **Drift Detection and Reconciliation**: Detecting and automatically reconciling any drift between deployed applications and the desired state.
    #. **Role-Based Access Control**: Defining and enforcing fine-grained access control policies for Argo CD users.
    #. **Application Management**: Managing the lifecycle of applications, including rollouts, rollbacks, and scaling.

Argo CD provides a simple and efficient way to manage applications deployed in a Kubernetes cluster while ensuring that the deployed applications are always in sync with the desired state defined in Git.

==============
Install ArgoCD
==============

.. code-block:: bash

    kubectl create namespace argocd
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

Access The Argo CD API Server

.. code-block:: bash

    kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'

Port Forwarding

.. code-block:: bash

    kubectl port-forward svc/argocd-server -n argocd 8080:443

Login Using The CLI

.. code-block:: bash

    kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

Remove everything

.. code-block:: bash

    kubectl delete namespace argocd

========================
Create first application
========================

Steps to create a new application in the Portal:

    #. Click on the **New Application** button.
    #. Enter the application name.
    #. Enter the project name.
    #. Enter the repository URL.
    #. Enter the path to the application manifest.
    #. Select the cluster where the application will be deployed.
    #. Click on the **Create** button.