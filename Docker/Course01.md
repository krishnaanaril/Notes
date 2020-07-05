# Docker & Kubernetes: The Big Picture

## Container: Primer
### The Bad old days
The author was saying about how comapanies were under utilizing the servers they've purchased for running their apps. One server for one app.
### Hello VMware
Vmware and hypervisors provide some sort of efficency by running multiple apps in a single server.
### VM warts
The downside of hypervisors is that each one need separate OS and maintenances, plus shared resources of the server.
### Containers
Container have one common OS and do not have to share resources. It can boot up fast and light weight.
### Container: Demo
1. Download the image
2. Create a container from image
3. Verify that it is running
4. Stop the container
5. Restart the container
### Recap
* Cloud Native is all about how an application is built. You can run a cloud native app on on-premise setup.
* Containers are VM 2.0, but don't expect to replace VMs.

## Docker
### Docker the technology
It makes running the apps inside the container really easy.

## Kubernetes
### Kubernetes History
* K8s came from Googles inhouse tecnhologies Borg & Omega
* K8s can be run in cloud and on-prem.
* K8s can make the applicaiton cloud platfrom independent.

## Misc
* Docker & K8s can handle both stateless and stateful apps.
* Gameplan - describles the app, how services interact with each other and so on
* Give gameplan to orchestrator (k8s)
* Let orchestrator deploy and manage app.