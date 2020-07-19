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

### Creating Web UI Dashoboard in k8s Windows

* Choose `Docker` settings and enable k8s in it. This will enable `kubectl` command in powershell.
* Run the command `kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0/aio/deploy/recommended.yaml`. This may change in future, please refer the doc to get the more updated url.
* Run the command `kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | sls admin-user | ForEach-Object { $_ -Split '\s+' } | Select -First 1)` to get the bearer token.
* Run the command `kubectl proxy` to make the dashboard up.
* Navigate to `http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/` in your browser.
* A login screen will appear and paste the token their.
