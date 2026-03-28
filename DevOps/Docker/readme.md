# Docker Definition:
is an open-source platform that enables developers to **build, package, and run applications in containers**.

## Docker Workings
With Docker we **containerize OS, External Dependency, Application Dependency , Code.** When Dockerfile(Instructions) are given to docker it builds upon the instructions and creates a Docker Image.Open source distributed object storage service e.g., Garage(Free), seaweedfs (Free)

Docker file + Docker image = container

## Docker file:
A Dockerfile is **a text file that contains a set of instructions used by Docker to automatically build a container image**.

## Docker Image:
A Docker image is a **lightweight, standalone, and executable package that includes everything needed to run an application using Docker, such as code, runtime, libraries, and dependencies.**

## Docker Container:
When we provide docker a docker image and run that image a container is running or we can say **a running instance of a docker image is called docker container**.


## Process to run a same environment again:
We create a file where we need to list all the instructions on a dockerfile then we can use it for the future. Install OS then install Docker and provide the dockerfile which contains those instructions and docker will execute all the instruction>

## Docker Repository/Registry: 
A central storage **where docker images are stored**.e.g., **Docker hub**. 
