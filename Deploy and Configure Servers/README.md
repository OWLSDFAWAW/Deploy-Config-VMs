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

    Python Access to vSphere APIs     
        sudo apt install python3-pyvmomi

    Git
        sudo apt-get install git


Create encrypted variables within playbook run the commad below and past results into variable files
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