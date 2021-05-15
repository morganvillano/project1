# Automated ELK stack deployment

For the configuration of the network depicted below, the files in this repository were used. 

![image](https://user-images.githubusercontent.com/77647664/118346643-f9ca0980-b50a-11eb-8bb1-11c35f1333b8.png)


A live ELK deployment on Azure was generated through the use of these files. Also, the files can be used for recreation of the entire deployment as demonstrated in the picture above.

https://github.com/morganvillano/project1/blob/main/scripts/ansible/ElK.yml

These documents have the following: 

1. Description of Topology
2. Access Policies
3. ELK Configuration
- filebeat
- machines that are monitored 
- Ansible playbook


Description of the Topology

The networks main purpose is for exposing an instance of DVWA, that is both load-balanced monitored.

The load-balancer is used for ensuring the high availibility of the application as well as restricting access to the network.

- What aspect of security do load balancers protect? Wht is the advantage of a jump box?
-  The load balancers is is the availability and it helps keep people away from the network. It also helps protect against DoS attacks. One advantage to the jumpbox is that the administrator is the only one that has acess to it. This lets them connect to other machines within the networks. Finally, this reduces the number of attacks and reduces the attacks on the surface in case a person tries to take over the network.

Having the ELK server gives users the ability to easily monitor the VMs for changes to the   and system   .

What does Filebeat watch for? 
- the filebeat watches the SSH logins, the system logs and the sudo commands. 

| Name                 | Function                  | IP Address | Operating System |
|----------------------|---------------------------|------------|------------------|
| Jump-Box-Provisioner | Gateway                   | 10.0.0.5   | Linux            |
| Web1                 | Webserver                 | 10.0.0.7   | Linux            |
| Web2                 | webserver                 | 10.0.0.8   | Linux            |
| Web3                 | Webserver                 | 10.0.0.9   | Linux            |
| Elk-to-Red1          | Network Monitoring System | 10.1.0.5   | Linux            |

Access Policies: 

The machines interal networks are not exposed to the public internet.

The Jumpbox machine can make connections from the internet. You can only access this machine throguh the following IP addresses: 

- Only the administrator can access the jumpbox

The machines that are in the netowrk can only be accessed by Ansible container. 

- Which machine did you allow to access the ELK VM? What was its IP addess? 
-   IP address:

This table below is the summary of the access policies that are in place.

| Name                 | Publicly Acessible  | Allowed IP Addresses     |
|----------------------|---------------------|--------------------------|
| Jump-Box-Provisioner | YES (SSH)           | SSH with the Jump Box IP |
| Web1                 | NO (SSH) YES (HTTP) | 10.0.0.7                 |
| Web2                 | NO (SSH) YES (HTTP) | 10.0.0.8                 |
| Web3                 | NO (SSH) YES (HTTP) | 10.0.0.9                 |
| Elk-to-Red1          | NO (SSH) YES (HTTP) | 10.1.0.5                 |

ELK Configuration: 

The Ansible contaienrs were used to configure the ELK VM. The configurations were performed automatically. They are advantageous because..

TODO: what is the advantage of automatically configuring with Ansible?
- Through the implementation of version control, it allowed for the installation of certain software on the machines. In addition, alot of time was saved from manual installation of the software on all of the machines, that would have had to been done with the use of SSH. 

The implementation of the playbook:

- TODO: In 1-3 bullets, these are the steps to the ELK installation play. E.g., install Docker; download image; etc.
Step 1. Install docker.io
Step 2. Install pip3
Step 3. Install Docker python module

This screenshot shows the result of running sudo docker container list -a 


![image](https://user-images.githubusercontent.com/77647664/118346606-b1aae700-b50a-11eb-9442-557813b10097.png)


Machines and filebeats

The ELK server is here to monitor the following machines: 

TODO: List the IP addresses of the machines you are monitoring
- Web1 10.0.0.7
- Web2 10.0.0.8

These are the machines that the beats were installed on:

- This is the beat that was installed sucessfully: 
-   Filebeat

This beat lets us gather information from each machine:

- SSH logins, system logs, and sudo commands are collected by filebeat

Using the Playbook:

In order to use the playbook, you need to have the Ansible container running. 
 
 SSH into the control  and follow the steps below: 
 
 - Copy the /etc/ansible/filebeat-config.yml file to /etc/filebeat/filebeat.yml
 - update the /etc/filebeat/filebeat.yml and include the local host url for elastic ans kibana.
 - Run the palybook and go to http:/ipaddress:5601 to check that the installation worked as expected.

TODO: answer the following questions: 

- Which file is the playbook? Where do you copy it?
-  elk.yml and I copy it in the /etc/ansible/roles folder

- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- /etc/ansible/hosts and I would also create a server group and lists all the ip addresses below that. An exmaple would be if the elk machines have certain programs installed, I would label it as: 

[elk]
<insert IP addresses>

-_Which URL do you navigate to in order to check that the ELK server is running? 
- https://ipaddess:5601

A specific command the user will need to run abnd download the palybook, update the files, etc.
  - ansible-playbook <filename.yml> nano <filename.yml>
