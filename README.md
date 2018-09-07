# War file Deployment using nginx

This repository is used to deploy nginx and run the jar server in all machines specified in inventory file
It also adds a headder to proxy pass X-Glovo-Systems-Engineer-Candidate with default value as 1 along with real Ip and few other headders

## Setup
Perform the following steps in order to setup ansible controller machine (From where deployment are triggered)

Step | Command                    | Description
:--: | -------------------------- | ---------------
1.   | OS                         | CentOS 7
2.   | Download EPEL Repository   | wget http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-8.noarch.rpm
3.   | Enable rpm of EPEL         | rpm -ivh epel-release-7-8.noarch.rpm
4.   | Install Ansible            | sudo yum install ansible -y
5.   | Test Version               | ansible --version  (Tested with : 2.2.0.0)

## Configurations
Clone the deployment repository and do the following changes before running the ansible-playbook

    git clone https://github.com/naggappan/jar-glovo-deploy

## Environment: Production run
    
    vim production/group_vars/all/vars_file.yml   --> modify required parameters like download url 
    vim production/inventory --> provide IP address of all servers

## RUN
Following command is used to start the deployment process, This will install all required dependencies.
    
    cd jar-glovo-deploy 
    ansible-playbook -i production webservers.yml -vv 

Note: Your keys should be set for ansible user, if its different user then cange it in ansible.cfg
