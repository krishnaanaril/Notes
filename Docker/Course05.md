# Managing Docker Images

* Docker Hub - Public repository of images, both official and vendor supported images. 
* Docker Cloud - Hosted browser based administration interface for managing your own docker related resources.  
* Dokcer Trusted Registy is Doker's own premium image repository and part of enterprise service Docker Data Centre.
* Use `docker search` to search images in docker hub.

### Docker image best practices

* Building images from Dockerfile is better and gives you total control
* Specify the image version/tag during image pull.
* Keep it small: Docker images should be small to enough to do the task. 
* Single line RUN commands in dockerfile are better way to reduce the size of the image.