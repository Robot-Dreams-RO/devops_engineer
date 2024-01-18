################
9.2  Helm charts
################

==========
Definition
==========

Helm charts are a collection of files that describe a related set of Kubernetes resources. A single chart might be used to deploy something simple, like a memcached pod, or something complex, like a full web app stack with HTTP servers, databases, caches, and so on.

====================
Helm chart structure
====================

A chart is organized as a collection of files inside of a directory. The directory name is the name of the chart (without versioning information). The chart contains a metadata file that contains information about the chart, as well as a README file that contains optional documentation. The chart may also contain default configuration values, a default Kubernetes manifest file, and helper templates that, when combined, generate Kubernetes manifest files.

.. code-block:: bash

    $ helm create mychart
    Creating mychart

    $ tree mychart
    mychart
    ├── Chart.yaml
    ├── charts
    ├── templates
    │   ├── NOTES.txt
    │   ├── _helpers.tpl
    │   ├── deployment.yaml
    │   ├── ingress.yaml
    │   └── service.yaml
    └── values.yaml

    2 directories, 7 files
