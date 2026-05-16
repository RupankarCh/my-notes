# Setting up environment
```
docker login (To Log into a Docker registry like Docker Hub)
```


```
docker push username/image_name (→ Uploads your image to a registry (e.g., Docker Hub)

docker run -it <image_name> bash (To Create a new container from the image, Docker starts it, -it → gives you an interactive terminal session, bash starts a shell inside the container)

docker build -t <tag_name> . (To Build a Docker image from the current directory and -t tags it as <tag_name>)

docker run -p 2345:80 <tag_name> (To Run a container from <tag_name>, mapping port 2345 (host) to 80 (container))

docker run -d -p  3456:80 --name <container_name> <image_name> (To Run a container in detached mode, maps ports, and name it <container_name>)

docker ps -a (To List all containers (running + stopped))

docker tag <image_name> username/image_name:v2.0.3 (To Tag an image with a new name and version for pushing to a registry)
```
# A Basic Docker file
```
FROM → base image
RUN → install dependencies
COPY → add files
WORKDIR → set working directory
CMD → run the app
```
e.g.,
```
FROM ubuntu:latest (To Use the latest version of Ubuntu as the base image)

RUN apt update && apt install -y nginx (To Updates package lists and installs Nginx )

COPY . /app (To Copy all files from your local directory into /app inside the container.)





# Containerization Definition:
It is a **lightweight virtualization method that packages applications and their dependencies into isolated units** called containers, enabling consistent and efficient deployment across environments.container is an application.

## Benefits of Docker in compared to VM:
Containerization using Docker offers significant advantages over traditional Virtual Machines (VMs) by being more **lightweight, faster, and efficient**. Unlike VMs that require a full guest operating system, **Docker containers share the host OS kernel**, allowing them to start in seconds and use far fewer system resources. This leads to higher density on a single machine and better performance. Docker also ensures consistency across development, testing, and production environments, making it ideal for CI/CD pipelines. Additionally, **containers are highly portable and easier to manage, enabling faster deployment and scaling of applications compared to VMs.**

# Docker Definition:
is an open-source platform that enables developers to **build, package, and run applications in containers**.

## Docker Workings
With Docker we **containerize OS, External Dependency, Application Dependency , Code.** When Dockerfile(Instructions) are given to docker it builds upon the instructions and creates a Docker Image.Open source distributed object storage service e.g., Garage(Free), seaweedfs (Free)

Docker file + Docker image = container

## Docker file:
A Dockerfile is **a text file that contains a set of instructions used by Docker to automatically build a container image**. From that image we can run our containers.

## Docker Image:
A Docker image is a **lightweight, standalone, and executable package that includes everything needed to run an application using Docker, such as code, runtime, libraries, and dependencies.**

## Docker Container:
When we provide docker a docker image and run that image a container is running or we can say **a running instance of a docker image is called docker container**.


## Process to run a same environment again:
We create a file where we need to list all the instructions on a dockerfile then we can use it for the future. Install OS then install Docker and provide the dockerfile which contains those instructions and docker will execute all the instruction>

## Docker Repository/Registry: 
A central storage **where docker images are stored**.e.g., **Docker hub**. 

# Usage Tips:
- You can add the current user to the docker group to avoid typing sudo prefix.
- Images:(A binary/hepty file)
- hello-world (It is hello world docker image)
- docker/getting-started (It is Docker documentation image)
- debian (It’s a type of dependency In the context of Docker and a Dockerfile, a Debian dependency typically refers to a software package or library that is required for your application to run, and it's installed from Debian's package repositories. U can think of it like an library to install tools and libraries)
- FROM: Lets us create a new build stage from a base image(Imagine each image adds something new then base image is the Previous image)
- RUN: Lets us execute commands before starting the container.(remember to add -y to those command which asks for permissions)
- VOLUME: Lets us create a mount point where we can later connect a folder from the host machine.
- EXPOSE <port_number>: Lets us determine which port to listen on for our application.
- CMD: It lets specify default commands when the container starts to run.
- ADD, COPY: These allows us to copy data from our main machine to our container.


# Commands

```
#docker –help (To see the help menu and see if docker is installed in your system)

#apt install docker-compose (To install docker compose infrastructure)

#apt install docker.io (To install docker)

#docker search <container_name> (To search for an image in Docker Hub)

#docker images (To check all docker images stored locally on your system)

#pull (To download image from Docker Hub)

#rm (To remove container)

#rmi (To remove image)

#build (To build the image according to the instructions in the Dockerfile)

#exec (To execute command inside container)

#docker build -t <imagename> <path> (To create a new image)(If u r in the path of the Dockerfile then u can use dot(.))(U can directly run an image without the need of pulling it)

#docker pull <Image_name> (To pull a image from docker hub)

#docker run <image_name(hello-world)> (To run a docker image which is already downloaded locally, If not then this command will automatically contact the docker daemon,pull the image, docker daemon will create a new container from that image then the docker daemon streamed that output to the docker client which is sent to the terminal)

#docker run nginx -d -p 8123:80 (To launch container from nginx image with forwarded port and in detach mode. On outside the container on any machine connected to the network on browser go to localhost:<portname_Outside_one(8123)> nginx web page will open to us and using curl http://localhost:<Listening_port(80)> On the container terminal will open that same web page and if you somehow installed a browser which is GUI the same command will show the same webpage to you.)


#docker exec -it <container_name> /bin/bash (To  run a bash terminal in a running container, container name can be found on “docker ps” command)

#docker ps (To to list all currently running Docker containers.)
#docker ps -aq (To see history of started containers, we can add -a option shows all containers we ever launched, adding -q  shows only container IDs)

#docker stop <CONTAINER_ID> (To stop a container u can see container ID using sudo docker ps command)

#docker rm <container_ID> (To delete a container from ps -a, A running container can’t be deleted, U can add -f to delete an container forcefully)

#docker rm $(docker ps -aq) (To delete all containers, Here command in parenthesis outputs container IDs and it go thought deletion one by one)

#docker rmi <Imagename/ImageID> (To delete an image)

Options:
-dp 80:80 (this option is used with the run command when we want to run a docker image on our local host like a website in a browser.In the background)
-d (this option detach or run the process in the background)
-p <port_number(8123:80)> (This option is used to map a port, first port number is outside the computer and 2nd one is inside the computer)

```

# Wordpress Website Making:
```
mkdir wp_site
cd wp_site/
nano docker-compose.yml (nano gives us syntax highlighting)
<projectname>:
	image: <project_image>
	links:
	  -  <Other_project/container_name>:mysql
	environment:
	ports:
	volumes:
   -   <directoryonourhostmachine>:<directory inside the container>
```
   <img width="355" height="326" alt="image" src="https://github.com/user-attachments/assets/fda154bb-01ae-4da9-8b6e-572d4b73aa0c" />


#docker-compose up -d (To run a docker compose file in the background)(U can open it on browser “localhost:80”

Images:
wordpress:
mariadb: 

environment variable lets us define various parameters environment variables, logins, passwords and so on.


YML extension is a type of text file format where we write instructions in the form key colon value, indentation is crucial.You can create multiple container inside an yml file.

MariaDB:Using MYSQL takes subscription as it's owned by Oracle while MariaDB is an free and open source alternative 


WORKDIR /app (To Set /app as the working directory for subsequent commands.)

CMD ["nginx", "-g", "daemon off;"] (To Runs Nginx in the foreground when the container starts)
```
