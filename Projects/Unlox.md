# Module 1
start basic amazon linux in EC2 with all traffic
connect to it doing ssh
```
sudo dnf update -y
sudo dnf install nginx -y
sudo systemctl enable --now nginx
sudo systemctl status nginx
mkdir mini-shop
cd mini-shop
nano index.html
```
```
<!DOCTYPE html>
<html>
<head>
    <title>MiniShop</title>
</head>
<body>
    <h1>MiniShop Cloud Store</h1>

    <div>
        <h2>Product 1</h2>
        <p>Price: ₹500</p>
        <button>Add to Cart</button>
    </div>

    <div>
        <h2>Product 2</h2>
        <p>Price: ₹1200</p>
        <button>Add to Cart</button>
    </div>
</body>
</html>
```
CTRL+X → Y → ENTER
```
sudo cp index.html /usr/share/nginx/html/
sudo systemctl restart nginx
```
http://YOUR_PUBLIC_IP (verify)

```
sudo dnf install docker -y
docker --version
sudo systemctl enable --now docker
sudo systemctl start docker
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








