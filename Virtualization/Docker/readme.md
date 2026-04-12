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

WORKDIR /app (To Set /app as the working directory for subsequent commands.)

CMD ["nginx", "-g", "daemon off;"] (To Runs Nginx in the foreground when the container starts)
```
