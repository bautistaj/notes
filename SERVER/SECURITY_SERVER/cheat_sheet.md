# 🛡️ Linux Server Security Cheat Sheet  

## 👤 User Management

```bash
# Create non-root user
sudo adduser admin
sudo usermod -aG sudo admin
su - admin
````

## 🔐 SSH Security

```bash
# Edit config
sudo nano /etc/ssh/sshd_config
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes

# Restart SSH
sudo systemctl restart sshd

```

## Generate & add SSH key

```bash
# On local machine
ssh-keygen -t rsa -b 4096 -C "your@email.com"
cat ~/.ssh/id_rsa.pub

# On server
mkdir -p ~/.ssh && chmod 700 ~/.ssh
echo "your_public_key_here" >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys

```

## Test connection

```bash
ssh admin@your_vps_ip

```

## 🚫 Fail2Ban

```bash 
sudo apt update && sudo apt install fail2ban -y
sudo systemctl enable --now fail2ban
sudo fail2ban-client status sshd
```

## Check blocked IPs:

```bash 
sudo fail2ban-client status sshd

```

## 🔥 Firewall (UFW)
```bash
# Default policies
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

# Allow services
```bash
sudo ufw allow 22   # SSH
sudo ufw allow 80   # HTTP
sudo ufw allow 443  # HTTPS
sudo ufw allow 5432 # PostgreSQL (if needed)
````

# Enable + check
```bash
sudo ufw enable
sudo ufw status numbered

````

## 🔍 Verify Setup
```bash
# Active connections
ss -tuln
````

# Logs
```bash
sudo tail -f /var/log/auth.log

```

## ✅ Security Checklist

✅ Non-root sudo user created
✅ SSH keys configured, passwords disabled
✅ Fail2Ban installed and active
✅ UFW firewall configured
✅ Logs and connections verified