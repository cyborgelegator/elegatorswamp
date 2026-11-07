# Creating an SSH Key
```
ssh-keygen -t ed25519 -C "your_email@example.com"
ssh-copy-id remote_user@www.hostname.com
```
# Creating a VPS Firewall
Configure the VPS firewall at: VPS > Manage > Security > Firewall > Add Firewall

# Creating a Non-Root Admin User
```
useradd username
usermod -aG sudo username
```
# Disabling Root and Password Login

# Updating the hostname
```
hostnamectl set-hostname new_host_name
nano /etc/hosts
```
Replace the existing hostname in the hosts file, save and close the file.
```
reboot
```

# Updating Game Panel Hostname
