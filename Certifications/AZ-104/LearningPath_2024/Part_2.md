## Prerequisities for Azure administrators

- By default, Azure Cloud Shell sessions run in a container in a Microsoft network that's separate from your resources. Commands that run inside the container can't access resources in a private virtual network. For example, you can't use Secure Shell (SSH) to connect from Cloud Shell to a virtual machine that has only a private IP address, or use kubectl to connect to a Kubernetes cluster that has locked down access.
- To provide access to your private resources, you can deploy Cloud Shell into an Azure virtual network that you control. This technique is called virtual network isolation.
- The **Azure Relay** service enables you to securely expose services that run in your corporate network to the public cloud.

## Azure Resource Manager

- ARM works in the following way: If the resource already exists and no change is detected in the properties, no action is taken. If the resource already exists and a property has changed, the resource is updated. If the resource doesn't exist, it's created.