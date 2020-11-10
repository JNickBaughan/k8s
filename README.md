# Kubernetes

### basics

Kubernetes is a system from running many different containers over multiple different machines

It is used when we need to run many different containers with different images

miniKube is used for development ONLY, it sets up a small cluster on your local machine

In production we would use a managed solution such as Amazon Elastic Container service for Kubernetes (EKS) or Google Cloud Kubernetes Engine (GKE)

kubeCTL is used to manage the minikube virtual machine or to manage a production solution

Steps to setup local kubernetes development environment

1. Install KubeCTL
2. Install virtualBox, a Virtual Machine driver
3. Install miniKube

### yaml config files

Config files are used to create objects
Each file is fed into kubeCTL to create these objects

The “kind” setting on the yaml config is used to specify the type of object

Pod -> used to run a container
Service -> used to setup networking

The “apiVersion” -> this limits the scope of types we can use
V1 allows [ componentStatus, configMap, Endpoints, Event, Namespace, Pod, plus more ]

apps/v1 allows [ ControllerRevision, StatefulSet ]

### What is a pod?

After installing miniKube and running the start command a new virtual machine is running on my local environment. This VM is known as a node.

kuberenetes uses this node to run different objects.

use kubeCTL to load our yaml file and create a pod on the node

a pod is a grouping of containers with a specific purpose

why would
