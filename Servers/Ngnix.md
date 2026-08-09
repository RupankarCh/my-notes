# Nginx Server Notes & Maintenance Cheat Sheet

## 1. What is Nginx?

**Nginx (pronounced “Engine-X”)** is a high-performance web server and reverse proxy commonly used for:

* Hosting static websites
* Reverse proxying applications
* Load balancing
* SSL/TLS termination
* API gateway/proxying
* Serving multiple websites using virtual hosts
* Caching and compression

Typical architecture:

```text
Client
   │
   ▼
Internet
   │
   ▼
Nginx :80 / :443
   │
   ├── Static Files
   │
   └── Reverse Proxy
          │
          ├── Node.js :3000
          ├── Python :8000
          └── Java :8080
```

---

# 2. Important Nginx Locations

### Configuration

| Path                          | Purpose                               |
| ----------------------------- | ------------------------------------- |
| `/etc/nginx/nginx.conf`       | Main Nginx configuration              |
| `/etc/nginx/conf.d/`          | Additional configuration files        |
| `/etc/nginx/sites-available/` | Available virtual-host configurations |
| `/etc/nginx/sites-enabled/`   | Enabled virtual hosts                 |

### Logs

| Path                        | Purpose             |
| --------------------------- | ------------------- |
| `/var/log/nginx/access.log` | Client/request logs |
| `/var/log/nginx/error.log`  | Nginx errors        |

### Web files

Common locations:

```bash
/var/www/html
/var/www/
/usr/share/nginx/html
```

> Exact paths can vary depending on the Linux distribution and installation method.

---

# 3. Basic Service Management

### Check Nginx status

```bash
sudo systemctl status nginx
```

### Start Nginx

```bash
sudo systemctl start nginx
```

### Stop Nginx

```bash
sudo systemctl stop nginx
```

### Restart Nginx

```bash
sudo systemctl restart nginx
```

### Reload configuration

```bash
sudo systemctl reload nginx
```

**Important:** Prefer `reload` after configuration changes when possible. It allows existing connections to finish while workers reload the configuration.

### Enable Nginx at boot

```bash
sudo systemctl enable nginx
```

### Disable automatic startup

```bash
sudo systemctl disable nginx
```

---

# 4. Configuration Testing

**Always test configuration before reload/restart.**

```bash
sudo nginx -t
```

Expected result:

```text
syntax is ok
test is successful
```

For more detailed configuration information:

```bash
sudo nginx -T
```

This dumps the complete loaded configuration.

### Recommended workflow

```bash
sudo nginx -t
sudo systemctl reload nginx
sudo systemctl status nginx
```

---

# 5. Nginx Version

```bash
nginx -v
```

Detailed build information:

```bash
nginx -V
```

Check installed package:

### Ubuntu/Debian

```bash
dpkg -l | grep nginx
```

### RHEL/CentOS/Rocky/AlmaLinux

```bash
rpm -qa | grep nginx
```

---

# 6. Virtual Host / Server Block

A basic website configuration:

```nginx
server {
    listen 80;
    server_name example.com www.example.com;

    root /var/www/example;
    index index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }

    access_log /var/log/nginx/example_access.log;
    error_log /var/log/nginx/example_error.log;
}
```

After creating or modifying the configuration:

```bash
sudo nginx -t
sudo systemctl reload nginx
```

---

# 7. Reverse Proxy

A common configuration for an application running on port `3000`:

```nginx
server {
    listen 80;
    server_name example.com;

    location / {
        proxy_pass http://127.0.0.1:3000;

        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

Check whether the backend is listening:

```bash
sudo ss -lntp | grep :3000
```

Test backend directly:

```bash
curl http://127.0.0.1:3000
```

---

# 8. Useful `curl` Tests

### Test HTTP

```bash
curl -I http://example.com
```

### Test HTTPS

```bash
curl -I https://example.com
```

### Follow redirects

```bash
curl -IL https://example.com
```

### Verbose request

```bash
curl -v https://example.com
```

### Test a specific Host header

Useful when DNS isn't configured yet:

```bash
curl -I -H "Host: example.com" http://127.0.0.1
```

---

# 9. HTTP Status Codes

|  Code | Meaning               |
| ----: | --------------------- |
| `200` | OK                    |
| `301` | Permanent redirect    |
| `302` | Temporary redirect    |
| `400` | Bad request           |
| `401` | Unauthorized          |
| `403` | Forbidden             |
| `404` | Not found             |
| `405` | Method not allowed    |
| `408` | Request timeout       |
| `429` | Too many requests     |
| `500` | Internal server error |
| `502` | Bad gateway           |
| `503` | Service unavailable   |
| `504` | Gateway timeout       |

### Most common Nginx issue

**502 Bad Gateway**

Usually means:

```text
Client → Nginx → Backend
                 X
             Backend unavailable
```

Check:

```bash
sudo systemctl status nginx
sudo ss -lntp
curl http://127.0.0.1:3000
sudo tail -f /var/log/nginx/error.log
```

---

# 10. Log Management

### View access log

```bash
sudo tail -f /var/log/nginx/access.log
```

### View error log

```bash
sudo tail -f /var/log/nginx/error.log
```

### Last 100 errors

```bash
sudo tail -n 100 /var/log/nginx/error.log
```

### Search errors

```bash
sudo grep -i error /var/log/nginx/error.log
```

### Search HTTP 500 errors

```bash
sudo grep ' 500 ' /var/log/nginx/access.log
```

### Search HTTP 404 errors

```bash
sudo grep ' 404 ' /var/log/nginx/access.log
```

### Count status codes

```bash
awk '{print $9}' /var/log/nginx/access.log | sort | uniq -c | sort -nr
```

---

# 11. Monitor Logs in Real Time

```bash
sudo tail -f /var/log/nginx/error.log
```

Multiple logs:

```bash
sudo tail -f /var/log/nginx/access.log /var/log/nginx/error.log
```

Using `less`:

```bash
sudo less /var/log/nginx/error.log
```

Exit:

```text
q
```

---

# 12. Check Ports

### Check listening ports

```bash
sudo ss -lntp
```

### Check port 80

```bash
sudo ss -lntp | grep ':80'
```

### Check port 443

```bash
sudo ss -lntp | grep ':443'
```

### Check application port

```bash
sudo ss -lntp | grep ':3000'
```

---

# 13. Process Monitoring

### Nginx processes

```bash
ps aux | grep nginx
```

Better:

```bash
pgrep -a nginx
```

### CPU/memory monitoring

```bash
top
```

or:

```bash
htop
```

### System resource overview

```bash
free -h
df -h
uptime
```

---

# 14. Disk Space Maintenance

Check disk usage:

```bash
df -h
```

Find large directories:

```bash
sudo du -sh /var/* | sort -h
```

Check Nginx logs:

```bash
sudo du -sh /var/log/nginx/*
```

Find large files:

```bash
sudo find /var/log -type f -size +100M -ls
```

**Do not manually delete active logs without understanding your log rotation setup.**

---

# 15. Log Rotation

Check whether logrotate is configured:

```bash
ls -l /etc/logrotate.d/nginx
```

View configuration:

```bash
cat /etc/logrotate.d/nginx
```

Check logrotate status/history:

```bash
sudo cat /var/lib/logrotate/status
```

Force a logrotate run only when appropriate:

```bash
sudo logrotate -f /etc/logrotate.conf
```

---

# 16. SSL/TLS Certificate Checks

Check certificate with OpenSSL:

```bash
openssl s_client -connect example.com:443 -servername example.com
```

Check expiry date:

```bash
echo | openssl s_client -connect example.com:443 -servername example.com 2>/dev/null | openssl x509 -noout -dates
```

You should monitor:

```text
notBefore
notAfter
```

If using Let's Encrypt/Certbot:

```bash
sudo certbot certificates
```

Test renewal:

```bash
sudo certbot renew --dry-run
```

---

# 17. Firewall Checks

### UFW

```bash
sudo ufw status
```

Allow HTTP:

```bash
sudo ufw allow 80/tcp
```

Allow HTTPS:

```bash
sudo ufw allow 443/tcp
```

### firewalld

```bash
sudo firewall-cmd --list-all
```

Check whether HTTP/HTTPS are allowed:

```bash
sudo firewall-cmd --list-services
```

---

# 18. DNS Troubleshooting

Check DNS:

```bash
dig example.com
```

or:

```bash
nslookup example.com
```

Check specific record:

```bash
dig A example.com
```

Check HTTPS:

```bash
dig CNAME example.com
```

Useful test:

```bash
curl -I https://example.com
```

---

# 19. Permissions

Check web directory:

```bash
ls -lah /var/www/html
```

Check ownership:

```bash
ls -ld /var/www/html
```

Find permission problems:

```bash
namei -l /var/www/html/index.html
```

Avoid blindly using:

```bash
chmod -R 777 /var/www/
```

This is generally **not** a proper fix and can create security problems.

---

# 20. Common Nginx Errors

### Error: `bind() ... address already in use`

Check what is using the port:

```bash
sudo ss -lntp | grep ':80'
```

or:

```bash
sudo lsof -i :80
```

---

### Error: `permission denied`

Check:

```bash
ls -lah /var/www/
```

Also inspect:

```bash
sudo tail -f /var/log/nginx/error.log
```

On SELinux-enabled systems:

```bash
getenforce
```

---

### Error: `502 Bad Gateway`

Check backend:

```bash
sudo ss -lntp
```

Then:

```bash
curl http://127.0.0.1:3000
```

And:

```bash
sudo tail -f /var/log/nginx/error.log
```

---

### Error: `403 Forbidden`

Check:

```bash
ls -lah /var/www/example
```

Check Nginx configuration:

```bash
sudo nginx -T
```

Possible causes include:

* Incorrect permissions
* Missing `index` file
* Directory listing disabled
* Incorrect `root`
* SELinux policy
* Access restrictions

---

### Error: `404 Not Found`

Check:

```bash
sudo nginx -T
```

Verify:

```nginx
root /var/www/example;
```

Then verify the file exists:

```bash
ls -lah /var/www/example/
```

---

# 21. Configuration Backup

Before making major changes:

```bash
sudo cp /etc/nginx/nginx.conf /etc/nginx/nginx.conf.bak
```

For a configuration directory backup:

```bash
sudo cp -a /etc/nginx /etc/nginx.backup
```

A timestamped backup:

```bash
sudo cp -a /etc/nginx "/etc/nginx.backup.$(date +%F-%H%M%S)"
```

---

# 22. Safe Configuration Change Procedure

Use this procedure for production servers:

```text
1. Check current status
2. Backup configuration
3. Make configuration change
4. Test configuration
5. Reload Nginx
6. Check service status
7. Test website/API
8. Monitor error logs
```

Commands:

```bash
sudo systemctl status nginx

sudo cp -a /etc/nginx "/etc/nginx.backup.$(date +%F-%H%M%S)"

sudo vi /etc/nginx/nginx.conf

sudo nginx -t

sudo systemctl reload nginx

sudo systemctl status nginx

curl -I https://example.com

sudo tail -f /var/log/nginx/error.log
```

---

# 23. Maintenance Checklist

### Daily

```text
[ ] Nginx service running
[ ] Website/API accessible
[ ] Check error logs
[ ] Check HTTP 5xx errors
[ ] Check disk usage
[ ] Check CPU/memory if there are alerts
```

Commands:

```bash
systemctl is-active nginx
df -h
free -h
sudo tail -n 50 /var/log/nginx/error.log
```

---

### Weekly

```text
[ ] Review Nginx error logs
[ ] Check disk growth
[ ] Check log rotation
[ ] Review unusual traffic/errors
[ ] Check SSL certificate expiry
[ ] Verify backend services
[ ] Check firewall configuration
```

---

### Monthly

```text
[ ] Review Nginx version
[ ] Review OS security updates
[ ] Review SSL/TLS configuration
[ ] Review unused server blocks
[ ] Review configuration backups
[ ] Test certificate renewal
[ ] Review resource utilization
[ ] Verify monitoring/alerting
[ ] Test backup/restore procedures
```

---

# 24. Quick Troubleshooting Flow

When a website is down:

```text
                 Website Down
                      │
                      ▼
              Is Nginx running?
                 /          \
               NO            YES
               │              │
               ▼              ▼
       systemctl status    Test locally
       systemctl start    curl localhost
                              │
                              ▼
                       Check error.log
                              │
                    ┌─────────┴─────────┐
                    ▼                   ▼
                  502                  4xx
                    │                   │
                    ▼                   ▼
             Check backend       Check root/
             service/port        permissions/config
                    │
                    ▼
              Test backend
              with curl
```

---

# 25. Production Quick Commands

Keep these handy:

```bash
# Status
sudo systemctl status nginx

# Start
sudo systemctl start nginx

# Stop
sudo systemctl stop nginx

# Restart
sudo systemctl restart nginx

# Reload
sudo systemctl reload nginx

# Test configuration
sudo nginx -t

# Full configuration
sudo nginx -T

# Version
nginx -v

# Access log
sudo tail -f /var/log/nginx/access.log

# Error log
sudo tail -f /var/log/nginx/error.log

# Ports
sudo ss -lntp

# Disk
df -h

# Memory
free -h

# Processes
pgrep -a nginx

# Test website
curl -I https://example.com

# Test backend
curl http://127.0.0.1:3000

# SSL expiry
echo | openssl s_client -connect example.com:443 -servername example.com 2>/dev/null | openssl x509 -noout -dates
```

## Golden Rules

> **1. Always run `nginx -t` before reload/restart.**

> **2. Prefer `reload` over `restart` for normal configuration changes.**

> **3. Check `error.log` whenever something behaves unexpectedly.**

> **4. For 502 errors, check the upstream application first.**

> **5. Never blindly use `chmod 777` as a permissions fix.**

> **6. Back up production configuration before major changes.**

> **7. Monitor disk space because logs can eventually fill the filesystem.**

> **8. Keep SSL certificates, Nginx, and the underlying OS maintained.**

> **9. Test changes locally and externally where possible.**

> **10. Make changes small and reversible.**
