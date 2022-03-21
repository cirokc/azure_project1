# azure_project1
Repository for week 13 Project 1
Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

elk_playbook.yml
filebeat_playbook.yml
metricbeat_playbook.yml

This document contains the following details:

Description of the Topology
Access Policies
ELK Configuration

Beats in Use
Machines Being Monitored


How to Use the Ansible Build


Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.

Using a load balancer allows the us to protect against DDoS attacks by ensuring that there are several servers are ready to take the load if another one goes down. Uinsg a jumpbox to control this keeps it hidden from the public. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.

Filebeat monitors the log files for the machine and allows alerts to be set when sepcific undesirable behaviors are recorded in said logs.
Metricbeat records system data periodically so that you can monitor any suspicious activity based on how the machines are performing. 

The configuration details of each machine may be found below.


| Name    | Function  | IP Address | Operating System |
|---------|-----------|------------|------------------|
| Jumpbox | Gateway   | 10.0.1.4   | Ubuntu Linux     |
| DVMA1   | webserver | 10.0.1.5   | Ubuntu Linux     |
| DVMA2   | webserver | 10.0.1.6   | Ubuntu Linux     |
| Elk VM  | elkstack  | 10.0.1.7   | Ubuntu Linux     |








Access Policies
The machines on the internal network are not exposed to the public Internet.
Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

98.225.249.153

Machines within the network can only be accessed by _____.

Only the jumpbox can access the ELK VM. IP address 10.0.1.4. 

A summary of the access policies in place can be found in the table below.



| Name    | Publicly Accesible | Allowed  IP Addresses |
|---------|--------------------|-----------------------|
| Jumpbox | No                 | 98.225.249.153        |
| DVWA1   | No                 | 10.0.1.4              |
| DVWA2   | No                 | 10.0.1.4              |
| Elk VM  | No                 | 98.225.249.153        |











Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

You're able to quickly reproduce the setup as many times as needed for as many machines as needed. 

The playbook implements the following tasks:

Install docker.io - Installs docker

Install Python-pip - installs python pip3

Install docker container - installs the python docker module

Launch docker container: elk - starts up elk

Command: sysctl -w vm.max_map_count=262144

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.


Target Machines & Beats
This ELK server is configured to monitor the following machines:

DVWA1 - webserver1 - 10.0.1.5
DVWA2 - webserver2 - 10.0.1.6

We have installed the following Beats on these machines:

Filebeat - Collects data from the log files to monitor
Metricbeat - Logs system data to monitor

These Beats allow us to collect the following information from each machine:

Filebeat monitors the log files for the machine and allows alerts to be set when sepcific undesirable behaviors are recorded in said logs. All activity done on a system will create and record a log file. 
Metricbeat records system data periodically so that you can monitor any suspicious activity based on how the machines are performing. For example CPU usage and RAM usage. 


Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:

Copy the _____ file to _____.
Update the _____ file to include...
Run the playbook, and navigate to ____ to check that the installation worked as expected.

Which file is the playbook? Where do you copy it? The files labeled with the ending _playbook.yml are the playbooks. /etc/ansible/file/filebeat_playbook.yml. Note that the configuration files will have to be edited to match your machines ip address in order for it to run properly. 
Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? Edit the /etc/ansible/hosts file to have your specified elkserver/webserverr ip addresses
Which URL do you navigate to in order to check that the ELK server is running? http://<your_external_ip_here>:5601/app/kibana
