# Initial VPS Setup

Initial VPS setup includes taking basic steps to secure the VPS, adding a fiewall through Hostinger's hPanel, and other minor updates to the VPS configurations for ssh. It also includes setting the hostname for the VPS and for the game panel. 
## Creating an SSH Key
```
ssh-keygen -t ed25519 -C "your_email@example.com"
ssh-copy-id remote_user@www.hostname.com
```

## Creating a VPS Firewall
Configure the VPS firewall via the Hostinger hPanel: VPS > Manage > Security > Firewall > Add Firewall

## Creating a Non-Root Admin User
Create an admin user for managing the VPS remotely.
```
useradd username
usermod -aG sudo username
```
## Disabling Root and Password Login
Update the following lines of /etc/ssh_config:
```
PermitRootLogin no
```
Update the following lines of /etc/ssh/sshd_config.d//50-cloud-init.conf:
```
#PasswordAuthentication yes
```
Restart ssh
```
systemctl restart ssh.service
```

## Updating the hostname
Update the system hostname if needed.
```
hostnamectl set-hostname new_host_name
```
Replace the existing hostname in /etc/hosts..
Reboot the VPS
```
shutdown -r now
```

## Updating Game Panel Hostname
Update the game panel hostname to display in address bar when visiting the game panel.
```
sudo rm /etc/nginx/sites-enabled/default
sudo systemctl restart nginx

```
