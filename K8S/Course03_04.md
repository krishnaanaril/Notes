# K8s: Integrating Volumes and Multi-container Pods

* **Stateful application** - An application that creates and saves data that needs to be kept.
* K8S Persistent volume subsystem - Decouples data from application Pods and containers, and abstracts implmentation detail.
* Three major API objects in K8S ecosystem to make external storage available to pods & containers. 
    1. PersistentVolume
    2. PersistentVolumeclain
    3. Storageclass
* A PVC can bind to a PV that has equal or more storage but not less.
* Create Storage Classes according to business requirements and tech capabilities. 
* Storage Classes are immutable objects.
* Multi Container Patterns
    - Init pattern 
    - Sidecar pattern
    - Adapter Pattern
    - Ambassador Pattern
* Pods let us augment container in many ways.
    - Probes
    - Affinities
    - Restart Policies
    - Termination Control
* K8s gurantees that the init container runs before main container and only once.
* Init Container - Runs to completion before app container starts
* Sidecar container = Starts with app container and runs concurrently.
* RBAC - Role Based Access Control.

# K8s for developers: Moving to cloud

* There are two ways in which we can use k8s in cloud
    1. K8s on cloud Machines - Set up and manage the k8s infrastructure yourself.
    2. Managed K8s - Cloud porvider manages K8s infrastructure - we simply use it.
* Deploying to Azure K8s Service (AKS)
    1. Install azure cli and login  with your credentials.
    2. Create a container registry. 
    3. Create a AKS cluster and give access to the cluster to pull from registry.
    4. To update an image:
        a. we can build image in the local workstation and push
        b. Or we can upload as tar file and build it in the cloud
* Deploying to GKE
    1. Enable K8s Engine API, Install google cloud SDK andn configure gcloud CLI. Python is required for Google SDK.
    2. Create GKE Cluster.
    3. Scaling can be done with the help of kubectl
    4. Cleanup
        a. Delete service - kubectl
        b. Delete cluster - gcloud
        c. Delete images - gcloud