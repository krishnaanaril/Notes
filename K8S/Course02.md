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