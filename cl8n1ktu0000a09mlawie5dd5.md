## Kubernetes - Architecture Part1

Today we're going to learn about the **Control Plane** which is the main part of the Kubernetes [Cluster](https://d33wubrfki0l68.cloudfront.net/2475489eaf20163ec0f54ddc1d92aa8d4c87c96b/e7c81/images/docs/components-of-kubernetes.svg)

**KUBERNETES** - is vendor-agnostic orchestration engine and it can run on almost any cloud provider 

-	if your legacy application or software running for a long time maybe (running on hundreds of VMs) now there is a high chance that your containerized cloud-native microservices application runs on thousands of containers, with this in mind, say 👋 hello to Kubernetes 




## Control plane
![controlplane diagram.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1664452073590/-B46yEG5c.png align="center")
it's the brain of the cluster, it's a set of powerful components, Let's see what are those

### API server { }

Include an API server, schedular, control manager, cluster store (ETCD)

The API server is the grand central of Kubernetes 

All components only go through the cluster by communicating via the API all roads lead to API-server
	
It exposes restful API 

We submit the manifest file via POST, hand it over to HTTPS then it connects to the API exposed restful interface on port 443

In the Kubernetes world, YAML files are called manifest files, which hold the desired state of the application 
	
The manifest file contains
				
>  which image want to pull from the registry 

> how many pod replicas wants by the user

> which port to expose (your application) and many more...

All API requests are subject to authentication and authorization checks, once its done, files will be persisted in the cluster store and then the work is scheduled to the cluster

### Cluster store (ETCD) 

This is the only stateful part of the control plane if there is no cluster store (ETCD), there is no cluster 

> ETCD -> A distributed database for Kubernetes, which stores the configuration files (Your desired state of the cluster will store here)

It's a best practice to run 3-5 (ETCD) replicas in the cluster for HA
			
The default Kubernetes installation, [ETCD](https://kubernetes.io/docs/concepts/overview/components/) replicates for each new cluster for HA purpose
		
ETCD wants to handle data writes which are coming from multiple writes from the same value, and also originating from different sources to be handled, to accomplish this ETCD uses RAFT which is a consensus algorithm

### Control manager ⚙️

Its a controller of controllers, basically it loads and executes all the independent controllers and monitors them 

some of the controllers are deployment controller, replicaset controller, statefulset controller which will see in later blogs

each subset of controllers runs a background watch loop consistently watching the API server for changes

if any node/pod/container breaks, [Kubernetes](https://kubernetes.io/) gets a red alert, and it immediately takes the required action, to match the desired state which is declared by the user in the manifest file.
			
### Schedular 🗒️

It always watching API Server like (is there any work to be done?), its job is to find the right node

It finds the right node, by performing many **checks** on the node, for selecting the right 
node it performs a **ranking system**, a node with the highest ranking will be selected 

> To find whether the node is capable to run the container

first

> it checks whether the node is tainted 

> then whether affinity or anti-affinity rules are applied 

> is the desired port available or not?

> it checks how many resources it has

> how many tasks the node is running

> is this node already have the image?
					
a node that is *incapable* is simply *ignored*, a node with the **highest ranking** will be selected 

if the schedular can't find the suitable node it's marked as *pending*...

The Scheduler **isn't responsible for running **(containers/pods), 

*Note*: it's there to pick up the right nodes to run your application, that's the only responsibility it has

<h1></h1>

In the next part, I will cover the whole Architecture, have a great day guys!

❤️ Thank you for reading my blog, feel free to connect me on <a target = "_blank" href= "https://www.linkedin.com/in/krishnamohanyerrabilli"> LinkedIn </a> or <a target = "_blank" href= "https://www.twitter.com/K_Mohan_">Twitter</a>. 
