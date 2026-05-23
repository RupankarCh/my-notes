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
nano dockerfile
```
```
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
```
```
sudo docker build -t mini-shop .
sudo docker run -d -p 8080:80 mini-shop
```
public-ip:8080 and verify

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








