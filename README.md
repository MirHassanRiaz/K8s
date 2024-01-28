# K8s Architecture

![image](https://github.com/MirHassanRiaz/K8s/assets/53171887/6831024e-38ae-40da-9ab7-705c45683dbb)

Kubernetes
Kubernetes provides tools and functionality around orchestrating container workloads. Hence, Container orchestration.

Node:
Description: Think of a node as a worker machine in your Kubernetes cluster. It's where your applications run.
Analogy: Nodes are like individual workers in a factory, each responsible for carrying out specific tasks.

Pod:
Description: A pod is the smallest deployable unit in Kubernetes, representing one or more containers and shared resources.
Analogy: Imagine a pod as a small team of colleagues who work closely together to accomplish a specific job.

Container:
Description: A lightweight, standalone, and executable software package that includes everything needed to run a piece of software.
Analogy: Containers are like lunchboxes that contain everything (food, utensils, etc.) you need for a meal.

Deployment:
Description: Manages the deployment and scaling of applications, ensuring they run as intended.
Analogy: Deployment is like a manager overseeing the hiring and firing of employees to maintain optimal staffing levels.

Service:
Description: Exposes a set of pods as a network service, making it easy for other applications to find and communicate with them.
Analogy: Services are like receptionists who direct incoming calls to the right department within a company.

Namespace:
Description: Creates a virtual partition within a cluster, allowing multiple users or teams to share the same cluster without interference.
Analogy: Namespaces are like different floors in a building, each occupied by a different department, maintaining separation. A mechanism for isolating groups of resources within a single cluster.

ConfigMap:

Description: Holds configuration data that can be consumed by pods.
Analogy: ConfigMaps are like sticky notes on a fridge with important information for everyone in the household.
Secret:

Description: Similar to ConfigMap but specifically designed for storing sensitive information, like passwords or API keys.
Analogy: Secrets are like locked drawers where you keep important documents that only a few people should access.

# K8's Control Plane

 The control plane is the brain of the Kubernetes cluster, managing and coordinating all activities. Let's break down some key components of the Kubernetes control plane:

API Server:
Description: The API server is the gateway to the Kubernetes control plane. It exposes the Kubernetes API and processes RESTful requests to manage the cluster.
Analogy: It's like the front desk of a hotel where guests (users or components) interact with staff (control plane) to make requests.

Scheduler:
Description: The scheduler decides where to deploy new pods based on resource requirements, policies, and constraints.
Analogy: Think of it as an event planner deciding which team (node) should work on a particular task (pod).

Controller Manager:
Description: The controller manager runs controller processes, which handle routine tasks such as maintaining the desired state of the system.
Analogy: Similar to managers overseeing different departments and ensuring everything is running smoothly.

etcd:
Description: etcd is a distributed key-value store that stores the entire configuration and state of the cluster.
Analogy: Picture it as the central library where all information about the cluster's books (configuration and state) is stored.
These control plane components work together to maintain the desired state of the cluster, handle user requests, and ensure that applications run efficiently. The control plane is like the central nervous system, coordinating and directing the activities of the Kubernetes cluster.

Kubeadm:
Simplifies the process of building Kubernetes clusters. In simple words Kubeadm is a cluster setup tool. kubeadm does handle deployment or management of applications. kubectl or another application deployment service are typically used to handle this.

# Commands

## To list down all the PODS in Kubernettes System
$:kubectl get pods --namespace kube-system

## To list down all namespaces and PODS
$:kubectl get pods --all-namespaces

## To create namespace
$:kubectl create namespace dev

## To list namespaces
$:kubectl get namespace

## To list pods
$:kubectl get pods

## List kubectl namespace output to a file
$:kubectl get namespace > /home/cloud_user/namespaces.txt

## List kubectl namespace output to a file
$:kubectl get pods -n mobile-gateway

## List pods in each individual namespace
$:kubectl get pods -n mobile-gateway

## List all namespaces
$:kubectl get pods --all-namespaces

![image](https://github.com/MirHassanRiaz/K8s/assets/53171887/aba2a7ca-3fa1-41e3-8c14-535a2c16e5d9)

## Draining a Node
$:kubectl drain <node name>

## Ignore Daemonsets(pods tied to each node)
$:kubectl drain <node name> --ignore-daemonsets

## Check which pods are assigned to each node to plain draining of workder nodes
$:kubectl get pods -o wide

## Uncordon (brining a worker node from maintenance back to cluster)
![image](https://github.com/MirHassanRiaz/K8s/assets/53171887/d1bf79d1-f7d9-40c2-b4b4-87694ba0d842)

## Deleting deployment
$:kubectl delete deployment my-deployment

# Upgrade Kubernettes cluster with Kubeadm

## Draining a Node
$:kubectl drain k8s-control --ignore-daemonsets

## Removing held packages in Kubernetes
$:sudo apt-get install -y --allow-change-held-packages kubeadm=1.27.2-00

## Kubeadm upgrade plan for upgrading all components
$:sudo kubeadm upgrade apply v1.27.2

## Upgrade kubetctl
$:sudo apt-get update && \
$:sudo apt-get install -y --allow-change-held-packages kubelet=1.27.2-00 kubectl=1.27.2-00

## Reload Kubernettes services 
$:sudo systemctl daemon-reload
$:sudo systemctl restart kubelet
$:kubectl uncordon k8s-control

## Validate the upgraded nodes and their versions
$:kubectl get nodes

## Upgrade Kubernetes workers
$:kubectl drain k8s-worker1 --ignore-daemonsets --force
$:sudo apt-get update && \
$:sudo apt-get install -y --allow-change-held-packages kubeadm=1.27.2-00
$:sudo kubeadm upgrade node
$:sudo apt-get update && \
$:sudo apt-get install -y --allow-change-held-packages kubelet=1.27.2-00 kubectl=1.27.2-00
$:sudo systemctl daemon-reload
$:sudo systemctl restart kubelet
$:kubectl uncordon k8s-worker1

## What is etcd?
![image](https://github.com/MirHassanRiaz/K8s/assets/53171887/8ddf2d5e-99ee-458b-8210-7e00eff2daed)

## Backup etcd data?
![image](https://github.com/MirHassanRiaz/K8s/assets/53171887/5d8cc0f9-ca3b-4f6b-ac4f-a37a69f9326f)

## Restore etcd data?
![image](https://github.com/MirHassanRiaz/K8s/assets/53171887/b8db73a6-731a-4888-af95-79efabe3e134)


