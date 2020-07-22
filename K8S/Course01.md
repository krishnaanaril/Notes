## K8S for Developers: Core Concepts

* K8S is an open source system to manage deployment, scaling and management of containerised apps.
* An analogy for K8S is a conductor in an orchestra.
* Key K8S features:
    1. Service discovery/Load balancing
    2. Storage Orchestration
    3. Automate Rollouts/Rollbacks
    4. Self healing
    5. Secret and Configuration management
    6. Horizontal Scaling
* CLI for k8s is called `kubectl`
* kube-let
* kube-proxy
* Devloper use cases
    1. Emulate production environment
    2. Move from docker compose to k8s
    3. Ensure application scales properly
    5. Performance & end to end testing
* Similar to Docker which has client and server parts. `kubectl` is the client part of k8s. I've installed `kind` (k8s in docker) in ubuntu for cluster management.
* Pods and conatiners are only accessible within the K8s clusters by default. One way to expose a container port externally: kubectl port-forward
* If you delete a pod by `kubectl delete pod pod-name`, pod will be be deleted but k8s will create another one in place. To offically delete the pod we need to delete the deployment that created the pod.
* `kubectl run <deployment-name> --image=<image-name>` to create a pod based on the docker image.
* YAML files are composed of maps and lists. Indentation matters and always use spaces.
* `kubectl apply` can be used to create or update a resource.
* K8s relies on Probes to determine the health of a Pod container.
* Types of probes
    1. Liveness probe: When should a container restart?
    2. Readyness probe: When should a  container start receiving traffic?
* A ReplicaSet is a declarative way to manage Pods.
* A Deployment is a declarative way to manage Pods using a ReplicaSet.
* Deployments and ReplicaSets ensure Pods stay running and can be used to scale Pods.
* ReplicaSets act as a Pod controller:
    - Self-healing mechanism
    - Ensure the requested number of Pods are available
    - Provide fault-tolerance
    - Can be used to scale Pods
    - Relies on a Pod template 
* Use `--save-config` flag with `kubectl create`, if you want to use `kubectl apply` in the future.
* `kubectl scale deployment [deployment-name] --replicas=5` to scale a deployment.

### Creating Serivces

* Pods are "mortal" and may only live in a short time. You can't rely on a Pod IP address staying the same.
* Services do Pod load balancing 
* Services can be defined in differenct ways: 
 - ClusterIP - Expose the service on a cluster-internal IP (default)
 - NodePort - Expose the service on each Node's IP at a static port.
 - LoadBalancer - Provision an external IP to act as a load balancer for the service.
 - ExternalName - Maps a service to a DNS name

### Understanding Storage Options

* Q: How do you store application state/data and exchange it between Pods with K8s? A: **Volumes**
* A **Volume** can be used to hold data and state for Pods and containers
* A pod can have multiple Volumes attached to it.
* Containers rely on a mountPath to access a Volume.
* K8s supports:
 - Volumes
 - PersistentVolumes
 - PersistentvolumeClaims
 - StorageClasses
* A Volume Mount references a Volume by name and defines a mountPath
* AWS - Elastic Block Store - Cloud support for volume.

### Creating Web UI Dashoboard in k8s Windows

* Choose `Docker` settings and enable k8s in it. This will enable `kubectl` command in powershell.
* Run the command `kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0/aio/deploy/recommended.yaml`. This may change in future, please refer the doc to get the more updated url.
* Run the command `kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | sls admin-user | ForEach-Object { $_ -Split '\s+' } | Select -First 1)` to get the bearer token.
* Run the command `kubectl proxy` to make the dashboard up.
* Navigate to `http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/` in your browser.
* A login screen will appear and paste the token their.
