# Kubernetes for Developers: Deploy your code

* Scale deployment pods
    1. kubectl scale deployment [deployment-name] --replicas=5
    2. kubectl scale -f file.deployment.yml --replicas=5
    3. Update YAML files and do `kubectl apply`
* Deployments rely on replicasets to schedule and manage pods.
* One of the strengths of K8s is zero downtime deployment.