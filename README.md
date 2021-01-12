## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/dhernan1972/Cyber-Journey/blob/main/diagrams/Week12_Network_Diagram.jpg
https://github.com/dhernan1972/Cyber-Journey/blob/main/diagrams/Wk13_Network_Diagram.jpg

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Istall-Elk file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
* Description of the Topologu
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

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
*Installs docker.io: the Docker engine, used for running containers
*Installs python3-pip: Package used to install Python software
*Installs docker module: Python client for Docker
*Increases the virtual memory of the target VM in order to run the ELK container
*Downloads and launches the Docker container called sebp/elk:761
*Configures the container to start with the following port mappings:
  *5601:5601
  *9200:9200
  5044:5044
  
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
*Web-1
*Web-2
*Web-3

- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
*Filebeats
*Metricbeats
*Packetbeats

- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
