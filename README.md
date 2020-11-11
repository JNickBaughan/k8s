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

e.g. - a database container with support containers like logging and backup. An application and a database would not be in the same pod

in kubernetes we can only deploy a container in a pod

### client-pod.yaml -> creates a pod object

this file is creating a "pod" and we create one container within it

the ports property exposes port 3000 but we need the client-node-port.yaml to actually expose it to the outside world

metadata section name property is identifier used in kubeCTL

### client-node-port.yaml -> creates a service object

another type of object type in kubernetes is "Services"

services sets up networking in a kubernetes cluster

there are four types of subtypes of services [ ClusterIP, NodePort, LoadBalancer, Ingress ]

NodePort -> exposes a container to the outside world, only good for development purposes

browser connects to Kubernetes Node via kube proxy

kube proxy is built into kubernetes, it is the only window to the outside - decides where to route it

from there it goes to our service NodePort

our service NodePort will push our request to our pod via port 3000 and to our container

this is setup using the label selector system

client-node-port.yaml has a selector of component: web, this maps to client-pod.yaml metadata -> labels: component: web

label is arbitrary- it could be container: client, or pod: service - as long as they match

ports sections -> describes ports that need to be opened up on the target object

targetPort is identified to
port is
