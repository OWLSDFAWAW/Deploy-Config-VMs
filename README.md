This playbook, build the Microsoft domain and joins the member servers

Main role: Deploy the Virtual Machines

Setup the four Windows Servers (Primary Domain Controller, Replica Domain Controller, DHCP, Fileshare)
    Using the vSphere provider:
        Assign appropriate resources to each machine

Prerequisites

Linux machine with the following

    Ansible
        sudo apt update
        sudo apt install software-properties-common
        sudo add-apt-repository --yes --update ppa:ansible/ansible
        sudo apt install ansible

1. install below OS dependencies
2. copy resources
3. log out and back in to see venv build


ls 
```bash

# install dependencies for ubuntu
export DEBIAN_FRONTEND=noninteractive && sudo apt update && sudo apt -y upgrade \
  && sudo apt install -y sudo iputils-ping vim nano cifs-utils \
  && sudo apt install -y lsof socat rsync gnupg ntpdate show-motd \
  && sudo apt install -y git openssh-server python3.12-venv \
  && sudo apt install -y krb5-user sssd-krb5 gcc libkrb5-dev python3-dev


# copy resources 
sudo mkdir -p /resources/ansible-environment && sudo mkdir -p /etc/ansible/collections
cd resources
sudo cp -r ./* /resources/ansible-environment/
sudo cp ./ansible.cfg /etc/ansible/
sudo cp ./python-ansible-venv.sh /etc/profile.d/

sudo chown -R $USER:root /resources && sudo chown -R $USER:root /etc/ansible



Don't do these steps
    Python Access to vSphere APIs     
        sudo apt install python3-pyvmomi

    Git
        sudo apt-get install git


Create encrypted variables within playbook run the commad belpythonow and past results into variable files
replace id with variable name eg vsphere, replace password, replace variable with name ef vsphere_password
when prompted enter the same vault password for all entries in the playbook
copy the output and save in the group_vars/all.yml & host_vars/*
ansible-vault encrypt_string --vault-id id@prompt password --name variable

Example:
ansible-vault encrypt_string --vault-id ansible_pwd@prompt Pa55word --name ansible_password

Creating a mirror repo
sudo apt update sudo apt-get install apt-mirror

Edit configuration file
sudo vi /etc/apt/mirror.list uncomment out "set base_path" change deb line to deb-amd64 http://gb.archive.ubuntu.com/ubuntu jammy main universe comment out all other deb lines save and exit sudo apt-mirror


Create Vault file 
ansible-vault edit <file name>

Create a symbolic link
ln -s <path or source> <path of target>