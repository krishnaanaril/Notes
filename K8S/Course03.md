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