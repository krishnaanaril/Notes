# Kubernetes for Developers: Deploy your code

* Scale deployment pods
    1. kubectl scale deployment [deployment-name] --replicas=5
    2. kubectl scale -f file.deployment.yml --replicas=5
    3. Update YAML files and do `kubectl apply`
* Deployments rely on replicasets to schedule and manage pods.
* One of the strengths of K8s is zero downtime deployment.
![Rolling updates](./rolling_updates.png "Rolling updates")
* Deployments support two strategy options: 
    - Rolling update
    - Recreate (can result in down-time)
* --record option in `kubectl create` will record the command in the depolyment revision history.
* Several kubectl commands can be used for rollbacks:
    - kubectl rollout status
    - kubectl rollout history
    - kubectl rollout undo
* `kubectl rollout history` command to view the revisions available.
* Rolling updates are the default deployment strategy used by K8s.
* Canary deployment strategy involves deploying new versions of applications next to stable production versions to see how the canary version compares against the baseline before promoting or rejecting the deployment.
* A canary deployment involves 3 main K8s resources:
    - Service
    - Stable deployment
    - Canary deployment
* Blue/Green deployments, which may also be referred to as A/B deployments require two identical hardware envrionments that are configured exactly the same way. While one envrionment is active and serving end users, the other environment remains idle.
* New applicaiton (green) is deployed alongside the old application (blue).
* **Changing from blue to green**: Once a green deployment has been successfully rolled out and tested, change the public service's selector to 'green' using `kubectl set selector svc [service-name] 'role=green'`
* A job creates a Pod(s) that performs a task or batch process. Unlike standard Pods, a job doesn't run indefinitely.
* A cron job creates jobs on a time based schedule. Scheduled using cron format. Cronjob names must be less than 52 characters.
* Metrics Server is a cluster-wide aggregator of resource usage data. It is deployed by default in clusters created by kube-up.sh script as a deployment object.
* Key troubleshooting commands
    - kubectl get pod [pod-name] -o yaml
    - kubectl describe pod [pod-name]
    - kubectl exec [pod-name] -it sh  (to login to the shell of a pod)
* Viewing Pod logs
    - kubectl logs [pod-name]
    - kubectl logs [pod-name] -c [container-name]
* Masater kubectl commands that can help troubleshoot issues with Kubernetes resources.