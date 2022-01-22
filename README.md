# Project-1
MSU Cybersecurity Bootcamp Project 1: Elk-Stack
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

https://github.com/afreder23/Project-1/blob/main/Ansible/Filebeat/filebeat-playbook.yml  

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly protected, in addition to restricting traffic to the network. 
  Load balancers protect the servers from a denial-of-service attack. A load balancer distributes traffic amongst the servers. One benefit of using a jump box is that it protects your virtual machines from Publexposure.                                                                                                                                         


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
- _TODO: File beat watches for logfiles
- _TODO: Metric beat records the log files found by file beat

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | VM       | 10.0.0.7   | Linux ubuntu 18.4|
| Web-2    | VM       | 10.0.0.8   | Linux ubuntu 18.4|
| ELKSERVER| VM       |  10.1.0.4  | Linux ubuntu 18.4|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 209.249.25.60

Machines within the network can only be accessed by port 22.
- Jump Box VM 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  |204.249.25.60         |
| DVWA-VMs |     No              |   10.0.0.4           |
|Elk Server|       No            |     10.0.0.4         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible can be run from the command line and ensures there are no errors by running the same scripts everywhere.

The playbook implements the following tasks:
- Changes the memory of the ELKSERVER VM
- Installs docker.io 
- Installs python-pip 
- Installs the docker python module 
-Downloads and launches the new docker elk stack

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

 

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.4 
-10.0.0.7 
-10.0.0.8 
-10.1.0.4

We have installed the following Beats on these machines:
- filebeat-7.6.1-amd64.deb

These Beats allow us to collect the following information from each machine:
- _TODO: Filebeat is used to send your log files to Kibana. Filebeat is continually monitoring and collecting log events on specified servers.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat-configuration.yml file to ELKSERVER VM.
- Update the hosts file to include web servers 10.0.0.4, 10.0.0.7, 10.0.0.8 and update the elk server to include 10.1.0.4.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- The file book is filebeat-config.yml You copy the file from /etc/ansible/files/filebeat-config.yml to /etc/ansible/files/filebeat-config.yml 
- To make Ansible run the playbook on a specific machine you update the hosts file in /etc/ansible/hosts. In order to specify which machine to install the elk server or the filebeat you specify which hosts at the beginning of the playbook. 
- The URL you use to check that the elk server is running is http://[your.ELK-VMExternal.IP]:5601/app/kibana


