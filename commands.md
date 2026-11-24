
# Linux Server Setup — Commands

## 1. User Management

```bash
sudo adduser deploy
sudo usermod -aG sudo deploy
id deploy
groups deploy
```

## 2. SSH Configuration

```bash
sudo apt install openssh-server -y
sudo systemctl enable --now ssh
sudo systemctl status ssh
sudo sshd -t
sudo systemctl restart ssh
```

SSH connection test:

```bash
ssh deploy@192.168.1.9
```

## 3. Firewall Configuration

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
sudo ufw status verbose
```

## 4. Nginx Installation

```bash
sudo apt update
sudo apt install nginx -y
sudo systemctl enable --now nginx
sudo systemctl status nginx
```

## 5. Web Application

```bash
sudo mkdir -p /var/www/kai-app
echo "KAI DevOps App is running" | sudo tee /var/www/kai-app/index.html
```

## 6. Nginx Configuration

```bash
sudo nano /etc/nginx/sites-available/kai-app
sudo ln -s /etc/nginx/sites-available/kai-app /etc/nginx/sites-enabled/kai-app
sudo nginx -t
sudo systemctl reload nginx
```

## 7. Application Verification

```bash
curl -i http://127.0.0.1/
curl -i http://127.0.0.1/health
curl http://192.168.1.9
```

## 8. Logs

```bash
sudo tail -n 20 /var/log/nginx/access.log
sudo tail -n 20 /var/log/nginx/error.log
```
