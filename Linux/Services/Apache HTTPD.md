**Apache HTTPD** (often just called **Apache**) is a popular **open-source web server** developed by the Apache Software Foundation. In simple terms, it’s software that **receives requests from web browsers and sends back web content**.

# How it works

When you visit:

`https://example.com`

your browser sends an HTTP request to a web server. Apache HTTPD can:

1. **Accept the request**
2. Determine what resource was requested
3. **Serve a file** such as HTML, CSS, JavaScript, or an image
4. Or **forward the request to an application** such as PHP, Python, or another backend
5. Return the response to your browser

**Why is it called HTTPD?**

* **HTTP** = Hypertext Transfer Protocol
* **D** = daemon, meaning a background service on Unix/Linux systems

So **HTTPD essentially means “HTTP daemon.”**

The /etc/httpd/conf.d directory contains modular configuration files for the Apache web server. Apache automatically reads every file in this folder ending in .conf when it starts up.
Common Content:
- sssl.conf: Configures HTTPS security settings and SSL/TLS certificates.
- welcome.conf: Controls the default Apache test page shown to users.
- Virtual Host files: Custom files (like mysite.conf) that route traffic to specific websites.
Module configs: Settings for third-party tools like PHP, python (wsgi.conf), or security modules.
- autoindex.conf: Formats the page users see when a directory has no index file.
- userdir.conf: Configures how user-specific directories are shared on the web

# Common things Apache can do

* Host websites
* Serve static files
* Handle HTTPS/TLS
* Configure virtual hosts (multiple websites on one server)
* Act as a **reverse proxy**
* Perform URL rewriting and redirects
* Provide authentication/access control
* Work with application servers such as PHP

A simplified architecture looks like:

```text
Browser
   │
   │ HTTP/HTTPS request
   ▼
Apache HTTPD
   │
   ├── Static files ──► HTML/CSS/JS/images
   │
   └── Reverse proxy ──► Backend application
                              │
                              ▼
                           Database
```

**Example:** If you have a Linux server running Apache and put `index.html` in its configured document root, Apache can deliver that page whenever someone requests your domain.

Apache HTTPD is one of the foundational technologies of the web and is still widely used, although servers such as **Nginx** and **Caddy** are also common today.


# Apache Web Server Configuration:

## IP Based
Configure IP Address, Subnet Mask, Gateway, yum repository
```
#yum install httpd -y
cd /var/www/html (The main public folder. It holds your website files like HTML, CSS, JavaScript, and images)
vim index.html (The Data website will contain)
systemctl enable httpd (To start httpd.service on every bootup)
systemctl start httpd
```
Now you can check the website by using the IP on ay browser.

## IP Based Virtual Host:
Configure IP Address, Subnet Mask, Gateway, yum repository
```
ifconfig ens160:1 192.168.10.11 (To create a virtual host)
ifconfig ens160:2 192.168.10.12
cd /etc/httpd/conf.d (To create Virtual Host files: Custom files (like mysite.conf) that route traffic to specific websites)
vim vhost1.conf
<VirtualHost 192.168.10.11:80>
DocumentRoot /var/www/html/vhost1
</VirtualHost>
```
Do same for vhost2.conf
```
cd /var/www/html
mkdir vhost1 (Creating separate directory to store website data for different virtual hosts)
mkdir vhost2
cd vhost1/
vim index.html (Store the website content)
```
Do same for vhost2
```
systemctl stop httpd.service
systemctl start httpd.service
```

## Domain Name Based
Configure IP Address, Subnet Mask, Gateway, yum repository
```
cd /var/www
mkdir site1
mkdir site2
cd site1/
vim index.html (Write the content of site1)
```
Do same for site2
```
cd /etc/httpd/conf.d
vim sites.conf
<VirtualHost *:80>
ServerName site1.com
DocumentRoot /var/www/site1
</VirtualHost>

<VirtualHost *:80>
ServerName site2.com
DocumentRoot /var/www/site2
</VirtualHost>

vim /etc/hosts
192.168.10.10 site1.com
192.168.10.10 site2.com

systemctl enable --now httpd
systemctl restart httpd.service
```
curl http://site1.com (To check site1.com's content






