# K8s Architecture

![image](https://github.com/MirHassanRiaz/K8s/assets/53171887/6831024e-38ae-40da-9ab7-705c45683dbb)

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
Analogy: Namespaces are like different floors in a building, each occupied by a different department, maintaining separation.
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

# Commands

# Command to list down all the PODS in Kubernettes
$:kubectl get pods --namespace kube-system
$:kubectl get pods --all-namespaces

# Command to create namespace
$:kubectl create namespace my-namespace
