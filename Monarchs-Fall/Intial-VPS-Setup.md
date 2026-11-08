# Initial VPS Setup

Initial VPS setup includes taking basic steps to secure the VPS, adding a fiewall through Hostinger's hPanel, and other minor updates to the VPS configurations for ssh. It also includes setting a scondary hostname for the game panel. 

## Creating a Non-Root Admin User

Create an admin user for managing the VPS remotely.
```
useradd username
usermod -aG sudo username
```

## Creating an SSH Key

Confirm the ability to log in as the new admin user over ssh.
```
ssh new_user_name@panel.example.com
```
Exit the VPS. Create an ssh key for connecting to the VPS without a password. A passkey is recommended but not strictly necessary.
```
ssh-keygen -t ed25519 -C "your_email@example.com"
ssh-copy-id remote_user@www.hostname.com
```
Confirm the ability to log in as the new admin user without a password. 

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

## Updating Game Panel Hostname

Update the game panel hostname to display in address bar when visiting the game panel.
```
sudo ampinstmgr setupnginx
```
When prompted, enter the panel's new fully qualified domain name.
When prompted, enter 8080 for the part.
The system will then obtain a new SSL certificate using certbot.

_NOTE: The old hostaame will still work, but you can now use this more memorable address._

## Creating a VPS Firewall

Configure the VPS firewall via the Hostinger hPanel: VPS > Manage > Security > Firewall > Add Firewall
