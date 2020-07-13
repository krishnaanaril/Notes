## Getting Started with Docker Swarm Mode
* Docker network helps container to communcate within the private network.
* docker-compose helps to have a declartive syntax to manage the containers in a single node.
* A docker service is a definition. It contains task templates, on which new containers are created. 
* If a container is stopped or shutdown, docker service will spawn a new container to match the configured replicas.
* To leave the swarm from a node, try `docker swarm leave`. If it is the last manager in the swarm add --force option.
* `docker node --availabilty=pause|drain` helps to move containers or tasks from one node to another.
* `docker service mode=global|replicated` - For replicated services, you specify the number of replica tasks for the swarm manager to schedule onto available nodes. For global services, the scheduler places one task on each available node that meets the service’s placement constraints and resource requirements. 
* Overlay network is a virtual network that is running on top of the underlay network.
* If you use 'docker service publish mode host', don't run multiple containers of the same serive in a node. This may cause port collision. Common mode is 'ingress', the other is 'host'.
* If the node is down, then we can easily remove the node. Else first leave from the swarm and then remove.
* Use 'watch' command (this command is not related to docker), to monitor the services. **Watch** command runs the given command every 2 seconds.
* User `docker service update` to rollout changes. Eg. version upgrade.
* On rolling upgrade a new task with updated version is created and kept in ready state. Once the previous task is shutdown, it automatically moved to running state.
* Docker serive version index is a global counter for all services, to keep track of the updates.
* `--rollback` flag with `docker service update` helps to rollback changes to the previous state. If we do it twice we reach the state in which we started. ie we can go back in history.
* Add public ports to security groups ingress rules to make it work in aws ec2 instances.
* `docker service update --env-add MYWEB_CUSTOMER_API=customer:3000 balance` - to add customer api load balancer end point to balance api.
* To have container to container communication, create an overlay network and add services to that. Do not publish port for the hidden api.
* To remove the internal load balancer, change the service endpoint mode from 'vip' to 'dnsrr'. 'dnsrr' is round robin via dns.
* Use `docker stack deploy` to deploy docker services using yml files. To remove use `docker stack rm`.
* When services are created by stack, a separate network will be created and we don't have to explicitly create another overlay network.
* Plain mapping between normal mode and swarm mode
    1. docker run -> docker service create
    2. docker-compose -> docker stack deploy
* The trifecta services
    1. Containers
    2. Networking
    3. Volumes
* To make the container automatically recover from failures, use health check options.
* Make use of `docker secret` to manage secret keys. To use `docker secret`, it must be a swarm manager.
* App reads secrets from '/run/secrets/x'


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
* A docker nodes availabilty depends on whether scheduler can assigns tasks. It doesnt' check whetther the node is down or not.