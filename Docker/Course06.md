# Containerizing a Software application with Docker

* Benefits of Microservices
    1. Low impact service upgrades
    2. Independently scaleable services
    3. Minimized failure risks
    4. Technological agnosticism when developing services
    5. Shallow learning curve
* Docker not only facilitates the microservices, but augment them too.
* What does a docker image provide 
    1. A filesystem with application code and dependencies.
    2. Metadata - Influences how a container runs
    3. A command - Gets executed as a process on invocation.
* There are two differenct techniques for creating docker images.
    1. committing a container
    2. Dockerfile instructions -  Preferred method
* Sequence for creating an image
    1. Choose a base image
    2. Derive a container
    3. Create a new image
* Choosing the right base image is important
* Is the image fit for purpose? What about it's integrity?
* Build step sequence
    1. Each build step uses the image produced by the previous step 
    2. A command is executed in a container derived from the image.
    3. The container is committed to a new image, before it is removed.
* Use `.dockerignore` file to exclude unnecessary content from being sent to daemon.
* Docker's build process maintains a cache of images referred to as the 'build cache'. The purpose of the build cache is to speed up the process.
* Place the commands in dockerfile in order to make the maximum use of buld cache.
* Purpose of **FROM** instruction is to specify base image. **FROM** instruction must be the first in a dockerfile.
* Keyword, **scratch** indicates build with no base image.
* **RUN** command executes command inside container.
* The concatenation of a command is considerd good practice and is acheived with a logical && shell operator.
* **HealthCheck** instruction defines command to test container health.
* The authoring of Docker images requires careful planning, in advance.
* Multi-stage builds use multiple FROM instructions. COPY instructions can reference content from a previous build stage.