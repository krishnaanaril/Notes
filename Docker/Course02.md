# Getting Started with docker

## Working with containers

* `docker ps` to list all the running conainers
* `docker ps -a` to list all the containers that exited.
* `docker images` to show info about images.
* In a standard docker install, we'll have the docker client and docker daemon on the same host.
* Client makes api call to daemon. Daemon implements the 'Docker Remote API'.
* If the docker daemon do not have a copy of image, it'll check the docker hub.
> The section 'Theory of Pulling and running containers' was very informative.
* Images ~ Stopped Containers
* Containers ~ Running Images
* `docker rm` to remove containers
* `docker rmi` to remove images
* `docker run -d <image>` detached mode
* `docker run -it <image>` interactive mode

## Swarm Mode Theory

* A cluster = A swarm
* Engines in a swarm run in 'swarm mode'.
* Manager nodes maintain the swarm. Anything more than 5 manager node is not advisable. Only one is leader.
* If you're not in swarm mode. You can't use services.
>  docker swarm join --token SWMTKN-1-2nr3lkw3ebxsv21bh4xsxnaxi5f6kahqopjfp968xn3ag4wiaz-ep1mv79ngdygk6sdociextvz4 192.168.43.192:2377

> docker swarm join --token SWMTKN-1-2nr3lkw3ebxsv21bh4xsxnaxi5f6kahqopjfp968xn3ag4wiaz-6q9eh5llbs50nnz71ptcewyk9 192.168.43.192:2377

* The setup of the tutor is 5 aws ec2 instances with docker installed. He then ssh into it and run the above commands. 
* Docker service is used to make sure that certain number of replicas are always running.
* Routing Mesh - Container aware routing mesh.
* Newly added docker nodes don't get the already existing tasks.
* Rolling updates is made possible with flags --update-parallelism & --update-delay. 
* `docker service update` command to update the service. Use --image flag to update the image.
* DAB stands for distributed application bundles

