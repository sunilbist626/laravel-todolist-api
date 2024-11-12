# Deploying New machine using Vagrant
This section defines the installation and initializing of the VM using vagrant and vmware workstation 

## Prerequisites
- Windows Machine
- Vagrant
- Vmware Workstation

## Setup Instructions
### 1. Install Vagrant
- Download Vagrant
- Run the installer and follow the prompts to complete the installation.
- Once installed, open a command prompt and verify the installation by running:
```sh
vagrant --version
```
### 2. Install VMware Workstation Provider Plugin for Vagrant
Vagrant requires a VMware provider plugin to work with VMware Workstation:
Install the Vagrant VMware plugin by running:
```sh
vagrant plugin install vagrant-vmware-desktop
```
### 3. Start the Vagrant Machine
Edit the Vagrantfile as per your customization and start the machine using Vmware Workstation.
```sh
vagrant up --provider=vmware_desktop
```
## Managing Vagrant Machine
### 1. Stop the Vagrant Machine
- Navigate to the directory containing your Vagrantfile
- Run the following command to gracefully stop the Vagrant machine:
```sh
vagrant halt
```
### 2. Delete the Vagrant Machine
- Navigate to the directory containing your Vagrantfile
-- Run the following command.
```sh
vagrant destroy
```
### 3. Remove Cached Boxes 
Vagrant keeps downloaded box files in a central cache, which can take up disk space over time. If you don’t plan to reuse the boxes in other projects, you can remove them.
- List all cached boxes by running:
```sh
vagrant box list
```
- Remove a specific box by running:
```sh
vagrant box remove box_name
```
