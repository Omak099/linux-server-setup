## Project Description

This project demonstrates the configuration of an Ubuntu Linux server
for hosting a simple web application.

The server was configured with SSH access, Firewall rules, Nginx,
a test web page, and a health-check endpoint.

## Evironment

- Os; Ubuntu 26.04.01 LTS
- Virtualization: Oracle VirtualBox
- Server IP: 192.168.1.9
- Web Server: Nginx

## Configuration

### 1. User Managment
- Created a separate user: deply
- Added deploy to the sudo group
- Configured SSH access

### 2. SSH Security
- Configured SSH access
- Root SSH login: 

### Firewall
- Enable UFM
- Allowed Ports:
	- 22/tcp - SSH
	- 80/tcp - HTTP
	- 443/tcp - HTTPS

### 4. Nginx
- Installed Nginx
-Enabled automatic startup
- Configured the web root:
	/var/www/kai-app

### 5.Health Check
Endpoint: /health

Expected response:
OK

HTTP status: 200

### 7. logs
- Nginx access log
- nginx error log

## Verification

```bash
sudo ufw status verbose
sudo systemctl status nginx
sudo systemctl is-enabled nginx
curl http://192.168.1.9
curl http://192.168.1.9/health
sudo tail -n 20 /var/log/nginx/access.log
sudo tail -n 20 /var/log/nginx/error.log
