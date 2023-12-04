# Kubernetes - k8s

##### Docker - Containerization platform (application code + dependencies) :> Docker is a tool designed to make it easier to deploy and run applications by using containers.

### :: Containers : allows a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and ship it all out as package.

##### Kubernetes - Orchetration platform (used to manage containers)
   
   ##### Note : Orchetration -> means management ( process which is used to manage our containers )
   
   ### Container Orchetration tool or engine automates depoying, scaling and managing contanerized application on a grup of servers.
   e.g. Kubernetes, Docker Swarn, Apache Mesos Marathon.

## Kubernetes :
  - Open Source container orchetration tool.
  - Developed by Google
  - Helps manage containerized applications.
  - ### Kubernetes is a container management tool which manages containerized applications like applications available on container platform like Docker.

##### Kubernetes takes care of 
          - Deploying
          - Scheduling
          - Scaling
          - Load Balancing
          - Batch Execution
          - Rollbacks
          - Monitoring

## Features: 
  ### Automatic Bin Packing : (bean means server)
        - Kubernetes will take care of packaging available jobs (containers) in bins (servers) in most efficient way.
        - Kubernetes automatically packages your application and schedules the container based on the requirements and 
          resource available.
        - Automatically places the containers based on their resource requirements like CPU & memory (RAM) while not 
          sacrificing availibility.
        - It will also saves resources.
  ### Pods and Nodes :
        - When you specify a  Pod, you can optionally how much CPU and memory (RAM ) each  container needs. WHen Containers 
          have resource requests specified, the scheduler can make better decisions about which nodes to place Pods on.
  ### Service discovery & load balancing :
        $  How kubernetes organizes containers?
             - Kubernetes does not run containers directly, instead it wraps one or more containers into a higher-level 
               structure called Pod.
        $  A POD contains:
             - an application container (or, in some cases, multiple containers)
             - one storage resource for all containers
             - a unique network IP
          
        $$   A kubernetes service is a set of pods that work together.

           With this system, kubernetes has control over network and communication between pods and can load load 
               balance across them.
  ### Storage Orchestration:
         - Containers running inside a pod may need to store data, PODs can have a storage volumes
         - Usually a single volume is shared within all the containers in a POD.
         - Kubernetes allows to mount a storage system of your choice LOCAL, CLOUD (aws), NETWORK
  ### Self - Healing:
         - If container fails - K8s restarts the container
         - If Nod dies - replaces and reschedule containers on other nodes
         - If containner does not respond to user defined health check -> Kills the container

  ### Automated Rollouts & Rollbacks :
   #### Rollout : Deploy changes to the application or its configurations.
   #### RollBack : Revert the changes & restore to previous state.
   ##### Kubernetes ensures there is no downtime during this process.
   #### Kubernetes progressively rolls out changes to your application or its configuration, while monitoring application health to ensure it doesn't kill all your instances at the same time. If something goes wrong Kubernetes will RollBack the changes for you.

  ### Secret and Configuration Management :

  #### Secret:
- In Kubernetes sensitive data like passwords, keys, tokens are handled using secrets.
- Secrets in Kubernetes created outside PODs & Containers.

#### Config Maps :
- In Kubernetes configurations are handled using Config Maps.
- Config maps in Kubernetes created outside PODs & Containers.

##### Secrets and Config Map are a kubernetes objects that seperated sensitive data and configurations respectively from PODs and Containers.
##### Secrets and configurations are stored in ETCD, it is a key-value datastore(database) - size limit 1MB

### Batch Execution :

### Horizontal Scaling :

## Architecture of Kubernetes:

##### When you deploy Kubernetes, you get a cluster.
##### A cluster is a set of machines, called NODEs.
##### A cluster has at least one [WORKER NODE] and at least one [MASTER NODE].
##### There can be more than one master nodes in the cluster to provide a cluster with failover and high availability.
##### There can be multiple clusters in Kubernetes architecture.

https://images.app.goo.gl/KkseUgygTQqKKdNs8

