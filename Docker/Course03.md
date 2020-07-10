## Getting Started with Docker Swarm Mode
* Docker network helps container to communcate within the private network.
* docker-compose helps to have a declartive syntax to manage the containers in a single node.
* A docker service is a definition. It contains task templates, on which new containers are created. 
* If a container is stopped or shutdown, docker service will spawn a new container to match the configured replicas.
* To leave the swarm from a node, try `docker swarm leave`. If it is the last manager in the swarm add --force option.

## Creating a docker swarm in AWS EC2
* Add an email subscription using **SNS**
* Add cloud watch for 10 usd billing and attached subscription to the SNS topic.
* Verified the email sent to the given address.
* Created a MFA for root account using Google authenticator. 
* Upgraded angular cli version 1 using pip3 (python)
* Added user credential to cli using 'aws configure'.
