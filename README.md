# Ansible-GetStarted

#Install Ansible on your ansible-master server

yum install epel-release
yum install ansible

#Configuring your Ansible Hosts

#The file is located in /etc/ansible/hosts

#Create Group Names and then add your servers
[group name]
xx.xx.xx.xx
yy.yy.yy.yy:10022

#Make sure you can login to the server via ssh without a password

#Generate a key using ssh-keygen on the ansible master and copy the id_rsa.pub key output to the /root/.ssh/authorized_keys in the target server

#Verify access using
ansible -m ping [group name]
#or
ansible -m ping xx.xx.xx.xx

#You should see below output for successful connection
xx.xx.xx.xx | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
}

#Run Playbook to install apache
ansible-playbook apache.yml
