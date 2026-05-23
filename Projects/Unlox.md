# Module 2
start basic Ubuntu in EC2 with SSH, HTTP, HTTPS allow and source 0.0.0.0/0
connect to it doing ssh
```
ssh -i cloudops-key.pem ubuntu@YOUR_PUBLIC_IP
sudo apt update && sudo apt upgrade -y
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx
cd /var/www/html
sudo rm index.nginx-debian.html
sudo nano index.html
```
```
<h1>CloudOps Enterprise Platform</h1>
<p>Module 1 Deployment Successful</p>
```
CTRL+X → Y → ENTER
```
sudo cp index.html /usr/share/nginx/html/
sudo systemctl restart nginx
```
CTRL + x
y
ENTER

http://YOUR_PUBLIC_IP (verify)

```
sudo apt install docker.io -y
docker --version
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl status docker
nano web-server
```
```
# Step 1: Use the lightweight, official Nginx base image
FROM nginx:alpine
# Step 2: Copy your local index.html file into Nginx's default web directory inside the container
COPY index.html /usr/share/nginx/html/index.html
# Step 3: Document that the container expects web traffic on port 80
EXPOSE 80
```
1. Stop your native host Nginx so Port 80 is completely free

sudo systemctl stop nginx

3. Build your new image with a clean name

sudo docker build -t web-server .

4. Run the container directly on Port 80

sudo docker run -d --name web-server-container -p 80:80 web-server

go to public-ip and verify

# Module 2

# Running instance
Creating instance:
Ubuntu, allow SSH, HTTP, HTTPS inbound security group traffic
```
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker
docker systemctl status docker
sudo docker run -d -p 80:80 --name my-web-shop rupankarch/my-nginx-app:v1
sudo docker exec -it my-web-shop /bin/sh (To get into the container)
cd /usr/share/nginx/html (To see the current html file)








