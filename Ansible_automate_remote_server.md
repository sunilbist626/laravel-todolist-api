# Ansible Setup and automate setup of remote server.
## Update your system
Make sure your system is up-to-date:
```sh
sudo apt update
sudo apt upgrade -y
```
## Install Ansible
The Ansible package is available in Ubuntu’s official package repository, but it might not be the latest version. To install the latest version, use the Ansible PPA.
### Add the Ansible PPA:
```sh
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
```
### Install Ansible:
```sh
sudo apt install ansible -y
```
### Verify Installation:
```sh
sudo ansible --version
```
## Configure Ansible Hosts
Define the remote servers you want to manage with Ansible by editing the /etc/ansible/hosts file.
```sh
sudo nano /etc/ansible/hosts
```
### Add your remote servers like this:
```sh
[servers]
server1 ansible_host=192.168.1.10 ansible_user=username
```
###  Test the Connection
Make sure that your Ubuntu machine can connect to the target servers via SSH. You can test the connection with:
```sh
ansible all -m ping
```
This command will ping all hosts defined in your inventory file. You should see "pong" responses if the connection is successful

### Passwordless authentication setup
To allow Ansible to communicate with remote servers, you typically use SSH keys for passwordless authentication. Here’s how to set up SSH keys and configure them for Ansible:
## Generate SSH Key Pair
On your control machine (Ubuntu 22.04 in this case), generate an SSH key pair if you don’t already have one:
```sh
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
- Press Enter to save the key in the default location (~/.ssh/id_rsa).
- You can set a passphrase for added security (optional).
## Copy SSH Key to Target Servers

To allow Ansible to connect without a password, copy the SSH key to each remote server:
```sh
ssh-copy-id username@server_ip
```
Replace username with the remote server’s username and server_ip with its IP address.

This command will copy the public key (~/.ssh/id_rsa.pub) to the remote server’s ~/.ssh/authorized_keys file, enabling passwordless SSH access.
## Test SSH Connection
```sh
ssh username@server_ip
```
### Configuring Remote server with php, php-fpm, nginx, mysql, redis
Ansible playbook to install PHP 8.3, PHP-FPM, Nginx, MySQL, and Composer on an Ubuntu 22.04 server. This playbook also creates a MySQL database named laravel and a user sunilbist@% with the password secret.
```sh
cd ~/application_dir/Ansible/
ansible-playbook -i your_inventory_file setup_web_server.yml
```
