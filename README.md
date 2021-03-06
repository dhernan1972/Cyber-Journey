## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/dhernan1972/Cyber-Journey/blob/main/diagrams/Week12_Network_Diagram.jpg
https://github.com/dhernan1972/Cyber-Journey/blob/main/diagrams/Wk13_Network_Diagram.jpg

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Istall-Elk file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
* Description of the Topology
* Access Policies
* ELK Configuration
* Beats in Use
* Machines Being Monitored
* How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting public access to the network.
The load balancer, from a security aspect, ensures that the website has protection from hackers throught the use of a Web Application Firewall(WAF), 
can be use to authenticate users and can protect against DDoS attacks.  The Advantage of using a jump box is it provides a single entry point 
connecting by way of Remote Desktop Protocol(RDP). The jump box provides acces to perform administrative duties.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to log files and system metrics.
Filebeat does the task of reading and indexing system and application log files, from the VM's, then sending them to either Elastisearch or 
Logstash. Metricbeats works by collecting system and server metrics as part of the ELK server.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Ubuntu 18.0.4    |
| Web-1    | Container| 10.0.0.5   | Ubuntu 18.0.4    |
| Web-2    | Container| 10.0.0.6   | Ubuntu 18.0.4    |
| Web-3    | Container| 10.0.0.7   | Ubuntu 18.0.4    |
| ELK      | Monitor  | 10.1.0.4   | Ubuntu 18.0.4    |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ELK machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
40.78.85.186

Machines within the network can only be accessed by each other. The Web-1, Web-2, and Web-3 VMs send traffic to the ELK server.


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 40.78.85.186         |
| Web-1    | No                  | 10.0.0.0/16          |
| Web-2    | No                  | 10.0.0.0/16          |
| Web-3    | No                  | 10.0.0.0/16          |
| ELK      | No                  | 10.1.0.0/16          |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because
it allows an administrator to automate creation, configuration and managment of multiple machines from one control machine.

The playbook implements the following tasks:

  * Installs docker.io: the Docker engine, used for running containers

  * Installs python3-pip: Package used to install Python software

  * Installs docker module: Python client for Docker

  * Increases the virtual memory of the target VM in order to run the ELK container

  * Downloads and launches the Docker container called sebp/elk:761

  * Configures the container to start with the following port mappings:
  
    * 5601:5601
  
    * 9200:9200
  
    * 5044:5044
    
https://github.com/dhernan1972/Cyber-Journey/blob/main/ansible/install_elk    
  
  


### Target Machines & Beats
This ELK server is configured to monitor the following machines:

  * Web1:10.0.0.5

  * Web2:10.0.0.6

  * Web3:10.0.0.7




The following Beats were installed and initiated to collect the following information from the target machines:

* Filebeats
  
  * Filebeat detects changes to the log filesystem. In this instance Filebeats was used in the collection of Apache logs.

* Metricbeats
  
  * Metricbeat detects changes in system metrics, such as CPU usage. For this project Metricbeats was used to CPU and RAM statistics, 
  failed attempts of privilige escalation and login attmepts through the SSH protocol.

* Packetbeats
 
  * Packetbeat collects packets that pass through the NIC, similar to Wireshark. We use it to generate a trace of all activity that takes place on the network,       in case later forensic analysis should be warranted.
 
 
The following playbooks were used to install Filebeat and Metricbeat on the Target VM's:

* https://github.com/dhernan1972/Cyber-Journey/blob/main/ansible/filebeat_playbook
* https://github.com/dhernan1972/Cyber-Journey/blob/main/ansible/metricbeat_cfg








### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install_elk.yml file to a new VM.
- Update the ansible hosts.yml file to create an ELK group and add the ELK server IP address. Specify which VM to install the playbook
  by configuring the install_elk.yml file to run on VM in the ELK group(host). This will ensure the install_elk.yml file on runs on a machine in 
  this specified group.  
- Run the playbook, and navigate to http://your-IP:5601/app/kibana#/home?_g=() to check that the installation worked as expected.


