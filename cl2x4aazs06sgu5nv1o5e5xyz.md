# Here's how Kubernetes makes your life easy

## What is Kubernetes?

Kubernetes is an open-source platform "Orchestration engine" mainly used to manage containerized applications, it is released by Google in 2014, and the project is donated to CNCF (Cloud-native computing foundation), primarily it serves micro-services applications, and it is still the world's second-biggest project in open source after Linux.

## Why use Kubernetes?

An orchestration engine helps to watch and control containerized applications very closely, and it is also used to automate certain functions, let me give an example for a better understanding of this broad topic, Let's say one of your application service's containers went down, it's not such a big deal to manually restart the container, but what if a large number of containers went down suddenly, wouldn't be easy this task will be automatically done, this is where Kubernetes comes, k8's will restart the containers, not only that it also provides many services such as logging, load balancing, secret, scheduling, scaling, fault-tolerance, deployment.

## Kubernetes architecture

![drf4dvoe6vmm615or8ol.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651551990773/sOUKXrQqp.png align="left")

### Brief

Kubernetes architecture has the master node, which is also called as control plane nowadays, which controls the nodes. these nodes are nothing but physical servers or VMs, which are run inside a data center applications are run inside the node, these nodes are previously called minions, In that, we have a lot of components such as type of service, cluster, pod.

### Master Node aka (Control plane)

![ucunhz25rnw5538zlw3j.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651578284007/COAsRgqlV.png align="left")

The Control plane acts like a mother to all worker nodes, It is responsible for doing many operations, such as scheduling worker nodes, and taking control of the whole cluster, majorly it has 4 components API server, control manager, etcd, scheduler, the primary component in the cluster is the API server which communicates with the host and many other parts in the cluster, the control manager takes control of the fault tolerance, and many more, such as if any pods(which we see in a bit), etcd holds our desired state data(YAML files which we see in a bit), and scheduler which schedules pods on available nodes.

### Components of the Master Node

#### API server

API server acts like the heart of the cluster, without API services we can't interact with k8's cluster, The role of the API server is to communicate with other components in the cluster, such as scheduler, etcd, control manager, kubelet, kube-proxy it's mandatory to communicate to have API server in between them.

#### Control Manager

The control manager's role is to It continuously checks whether the given desired state is running or not, suppose we want to deploy the application in 3 nodes, assume 3 pods have been allocated for three different nodes, now what if 1 pod is down, what if 3 pods have been down, there were control manager comes into rescue, it takes the information which provides by the node and the etcd, and checks whether the given state is equal to the current state, if it does not satisfy the desired state then the control manager restarts a new pod, by using different types of controllers.

There are 4 types of controllers beyond the control manager

* Node controller
    
* Replication controller
    
* Endpoint controller
    
* Service-token controller
    

#### Etcd

etcd holds the desired state, in the sense of key-value pairs stored for shared configuration, Kubernetes is a distributed system, so it wants a distributed storage to store the desired state, the desired state is nothing but a client requirement, and it also stores data about the current status, and metadata.

#### Scheduler

Its role is to assign pods to the nodes, its job is to check the suitable nodes by means of given constraints and available resources, then it schedules the pods to the nodes, it is done by following Kubernetes scheduling principles.

### Worker node

Its job is to run the containers in the pods on the node. a single node has multiple pods. worker nodes are part of the Kubernetes cluster.

![workernode.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651822654229/Rvr_qdPay.png align="left")

### Components of the worker node

#### Kubelet

kubelet is also called an agent node, because it lives on top of every node in the Kubernetes cluster, its main job is to take the pod spec from the API server, and after that, it talks to grpc (google remote procedure calls) over from the UNIX sockets and then the info goes through the runtime CRI (container runtime interface) shim (docker) and any other and then it creates pods as described in the pod spec, and it makes sure the containers are in the running state.

![ezgif.com-gif-maker.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651824921082/HPCzto8V2.png align="left")

Here the kubelet acts as the client, and CRI shim as the server.

#### kube-proxy

Its job is to direct the incoming requests from the client to the designated pods in the node, to the appropriate pods, but how is it possible through some service(a service is an object in Kubernetes) a service is worked by depending on some rules which are provided by Kube-proxy, based on these rules load balancing would be done.

![1_domcyQgFDDpdZHVMOXWn-g.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651826951957/VAoIrNppM.png align="left")

*A service load balances incoming requests between the backend pods. Photo by the Luc Juggery.*

#### Pods

A pod is the smallest unit in Kubernetes, like a container, is the smallest unit in the docker such as a pod in the K8. A pod's job is to run the containers inside it, containers are wrapped by a pod, and we interact and manage containers through the pod. there is an outline where we want to run multiple containers in the same pod, like one container helping another container.

#### Containers

This is where the real application is running, this is where the actual thing happens, we run containerized applications inside the containers, which are actually built by docker image, containers are basically invented to run micro-services, if you want to learn more about this you can check out my blog on Docker.

### Complete Architecture

![u2a7pghqkjuasfcjgha5.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651828282559/qGUgUUq69.png align="left")

### Installation

#### Play with K8s

If you want to start playing with k8's, or you want to test something in a Kubernetes environment, to this you don't pay any cloud provider, play with K8 is a playground that allows users to run K8s clusters in a matter of seconds, for any review purposes also you can use it, to get started you just need a docker or a GitHub account, for more information you can refer to this [link](https://labs.play-with-k8s.com/).

#### Minikube

This is my favorite one, Minikube helps to interact with Kubernetes in a local environment, it provides a single cluster, and the same system acts as a master as well as worker node, but this has 1 drawback this performance is fully based on your PC resources, which means it will be working with limited resources, to note Minikube is not for production environment. for more information on Minikube you can refer to this [Link](https://minikube.sigs.k8s.io/docs/start/)

#### Cloud Platforms

So many cloud providers can provide Kubernetes clusters by buying their resources, each cloud provider has its own Kubernetes model but under the hood, all work on the same principle, like aws has EKS(Elastic Kubernetes Service), Microsoft Azure has their own AKS (Azure Kubernetes Service), GCP has its GKE(google's Kubernetes engine), and Digital ocean has its DOKS(Digital ocean Kubernetes service) and many cloud providers have adopted k8's for their own functionality and for their different client needs.

#### More about Pods

Every node in the cluster has a unique IP address, and each pod inside the node has a dedicated IP address assigned to it, pods communicate with the outside world by using network namespaces this is assigned to the pods, and multiple containers share the same IP address inside the single node to communicate with each other, this also means they will share the same volumes, Cgroup limits, and even IPC names.

### Pod Networking

*how pods communicate with each other?*

* Inter-Pod communication: All the Pod IP addresses are fully routable on the Pod Network inside the Kubernetes cluster.
    

![l6jlt8ct10ivzouxhvso.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652001891718/i12MK4OtE.png align="left")

How do containers communicate in the same pod? Intra-Pod Communication: Containers use a shared Local Host interface. All the containers can communicate with each other’s ports on localhost.

![tmd0en6ob4bmndgg6693.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652002197988/_aSofHXu2.png align="left")

Thank you for reading my blog. Feel free to connect on [LinkedIn](https://www.linkedin.com/in/krishnamohanyerrabilli) or [Twitter](https://www.twitter.com/K_Mohan_).

Resources: https://youtu.be/KVBON1lA9N8 Thank you, Kunal Kushwaha 😊