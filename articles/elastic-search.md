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
- The set of nodes in the cluster
- All cluster-level settings
- Information about the indices in the cluster, including their mappings and settings
- The locations of all the shards in the cluster.
	
All this information can be found in the `ClusterState.java` file.

## 8. How does the node use unicast to discover an existing cluster?
Elasticsearch implements something called Zen discovery which is the built-in, default, discovery module. It uses unicast and file based discovery.
Zen discovery uses a list of `seed` nodes in order to start off the discovery process. When it starts, or when it’s electing a new master node, it iterates trough the list of nodes and try to connect to each one of them. It also holds up a conversation with each node and instruct them to find other nodes in order to get a complete picture of the cluster.

### 8.1 What information does it send?
It sends a static list of hosts for use as seed nodes. These hosts can be specified as hostnames or IP addresses

## 9. How does the cluster select a master node?
It’s done by a process named `Discovery` by which the cluster formation module finds other nodes with which to form a cluster. This process runs when you start an Elasticsearch node or when a node believes the master node failed and continues until the master node is found or a new master node is elected.

## 9.1 What code is executed?
From my understanding the following code is executed, whis is present in the class `ElasticSearchCluster` in the method `commonNodeConfig`
```java
private void commonNodeConfig() {
    final String nodeNames;
    if (nodes.stream().map(ElasticsearchNode::getName).anyMatch(name -> name == null)) {
        nodeNames = null;
    } else {
        nodeNames = nodes.stream().map(ElasticsearchNode::getName).map(this::safeName).collect(Collectors.joining(","));
    }
    ElasticsearchNode firstNode = null;
    for (ElasticsearchNode node : nodes) {
        // Can only configure master nodes if we have node names defined
        if (nodeNames != null) {
            if (node.getVersion().onOrAfter("7.0.0")) {
                node.defaultConfig.keySet()
                    .stream()
                    .filter(name -> name.startsWith("discovery.zen."))
                    .collect(Collectors.toList())
                    .forEach(node.defaultConfig::remove);
                node.defaultConfig.put("cluster.initial_master_nodes", "[" + nodeNames + "]");
                node.defaultConfig.put("discovery.seed_providers", "file");
                node.defaultConfig.put("discovery.seed_hosts", "[]");
            } else {
                node.defaultConfig.put("discovery.zen.master_election.wait_for_joins_timeout", "5s");
                if (nodes.size() > 1) {
                    node.defaultConfig.put("discovery.zen.minimum_master_nodes", Integer.toString(nodes.size() / 2 + 1));
                }
                if (node.getVersion().onOrAfter("6.5.0")) {
                    node.defaultConfig.put("discovery.zen.hosts_provider", "file");
                    node.defaultConfig.put("discovery.zen.ping.unicast.hosts", "[]");
                } else {
                    if (firstNode == null) {
                        node.defaultConfig.put("discovery.zen.ping.unicast.hosts", "[]");
                    } else {
                        firstNode.waitForAllConditions();
                        node.defaultConfig.put("discovery.zen.ping.unicast.hosts", "[\"" + firstNode.getTransportPortURI() + "\"]");
                    }
                }
            }
        }
        if (firstNode == null) {
            firstNode = node;
        }
    }
}
```
