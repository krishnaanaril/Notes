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
* Create VPC in an aws region
    * Not sure how to create the ipv4 CIDR blocks, I followed the aws developer - getting started tutorial in [plural sight](https://app.pluralsight.com/player?course=aws-developer-getting-started&author=ryan-lewis&name=aws-developer-getting-started-m3&clip=2). 
    * Add 0.0.0.0/0 as internet gateway in the VPC routing table. This is for outgoing traffic to reach the outside world.
    * This will automatically create a subnet, but there is also a provision to add multiple subnets.
* Command used to create the swarm maanger: `docker-machine create -d amazonec2 --amazonec2-vpc-id $AWS_VPC_ID --amazonec2-instance-type t2.micro --amazonec2-subnet-id $AWS_VPC_SUBNET --amazonec2-security-group docker-swarm-sg docker-swarm-manager`. Same command is used to create worker instances.
* Run `docker-machine ip docker-swarm-manager` and copy the address. Let it be 171.2.3.4
* Run `docker swarm init --advertise-addr 171.2.3.4:2377` to init the swarm manager.
* You can't run `docker node ls` from any of the worker nodes.
* It is better to add --advertise-addr and --listen-addr, eventhought i didn't do it for worker nodes.
* If you're exposing a port in a service (say 8080), add it to the inbound rule in security group. (Security group is like firewall)
* When a docker service is create with swarm across multiple nodes, a fully container aware load balancer is created called 'routing mesh'