# Elastic Search Questions
We want answer the question: *How a node is registered in a cluster?*, but first we have to have some foundation to get to that. Let’s begin.

## **1. What is ElasticSearch?**
ElasticSearch allows you to store, search, and analyze huge volumes of data quickly and in near real-time and give back answers in milliseconds. It’s able to achieve fast search responses because instead of searching the text directly, it searches an index.

## **2. What is a node?**
A node is a running instance of ElasticSearch which belongs to a cluster. Usually a node represents a single server.
There are several type of node roles, and a node can have multiple roles at the same time. The most important ones are:
- Master Node: Controls the cluster
- Data Node: Holds data and performs CRUD operations

## **3. What is a cluster?**
A collection of connected nodes.

Right now we know that our nodes are the responsible of handling our data. And that clusters are a collection of interconnected Nodes.
But we are still missing the main question.

## **4. What happens when a node is created?**
When a node is created it has to be assigned to a cluster. At startup, a node will use unicast to discover an existing cluster with the same cluster name and will try to join that cluster.

## **5. Remember master nodes?**
Each cluster has a single master node which is chosen automatically  by the cluster and can be replaced if it fails.

## **6. Node join request.**
During master election or when joining one existing formed cluster, a node sends a join request to the master in order to be officially added to the cluster. 
This is handled in the java class  `MasterNodeReadRequest.java` .

## **7. Cluster State**
Once a node has joined a cluster it’s registered in the cluster state, which is the metadata that represents the state of the whole cluster. It includes:
	* the set of nodes in the cluster
	* all cluster-level settings
	* information about the indices in the cluster, including their mappings and settings
	* the locations of all the shards in the cluster.
	
All this information can be found in the `ClusterState.java` file.
