---
description: This page describes how Logiq Observability Platform Organizes the logs.
---

# Nomenclature

Logs are organized by namespaces and applications and their processes.

### Namespace

The namespace is the top of the hierarchy. For a Kubernetes based deployment namespace maps to Kubernetes namespace and for non-Kubernetes based deployment it maps to the host-name of the virtual machine or physical host.

### Application & Process

In the Kubernetes based deployments Application refers to deployment name and process refers to its pod names. For example for Nginx application \(deployment/service\) may have multiple pods which are its processes. 

For the physical machine, the application refers to process names like Nginx or tomcat and process refers to process id.

