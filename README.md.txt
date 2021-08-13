## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/NicholasB-Collab/Demo/blob/main/Azure_Network_Diagram.drawio

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

Enter the playbook file. install_elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable, in addition to restricting traffic to the network.
What aspect of security do load balancers protect? What is the advantage of a jump box?
Load balancers protect each individual server from receiving more traffic than it can handle.

The advantage of a jump box is having a seperate device, off the web servers, to create new webservers as needed. This means that we do not have to open SSH ports on the web servers. Additionally, that the web servers do not need any parts of the operating system code that are not neccesary for their function.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.

What does Filebeat watch for?
Filebeat monitors locations and files, and pulls log events. In addition, Filebeat sends the files to Elasticsearch or Logstash for them to index.

What does Metricbeat record? Records of changes in system metics


The configuration details of each machine may be found below.


| Name        | Function | IP Address | Operating System |
|-------------|----------|------------|------------------|
| Jump Box    | Gateway  | 10.0.0.4   | Linux            |
| Web1        |Web server| 10.0.0.9   | Linux            |
| Web2        |Web server| 10.0.0.10  | Linux            |
| Web3        |Web server| 10.0.0.11  | Linux            |
| ELK         |Web server| 10.0.1.4   | Linux            |
|Load Balancer|Web server|  Static IP | Linux            |
| Work Station|Web server|  VM IP     | Linux
            |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
Hyper-V Virtual Machine's IP address

Machines within the network can only be accessed by SSH.
Which machine did you allow to access your ELK VM? What was its IP address?
I allowed:
Jump Box: 10.0.0.4
Workstation: Port 5601

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses   |
|----------|---------------------|------------------------|
| Jump Box | No                  | 10.0.0.1 10.0.0.2      |
| Web 1    | No                  | SSH Port 22, 10.0.04   |
| Web 2    | No                  | SSH Port 22, 10.0.04   |
| Web 3    | No                  | SSH Port 22, 10.0.04   |
| ELK      | No                  | Workstation on TCP 5601|
| Load Balance| No               | Workstation on 80 HTTP |                     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:

In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
	
	-Configue Elk Server
	-Download playbook
	-Update yml files
	-Run the playbook command

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-10.0.0.9
-10.0.0.10
-10.0.0.11 

We have installed the following Beats on these machines:
-Filebeat
-Meticsbeat

These Beats allow us to collect the following information from each machine:
The beats allow us to collect the following:
		Filebeat: Log Events
                Metricbeat: System Statistics and metrics
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the /etc/ansible/files/filebeat-config.yml' file to /etc/filebeat/filebeat-playbook.yml
- Update the playbook file to include https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.4.0-amd64.deb
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_
- Which file is the playbook? filebeat_playbook.yml /etc/ansible/files/filebeat-config.yml
- Where do you copy it? /etc/ansible/files/filebeat-config.yml
- Which file do you update to make Ansible run the playbook on a specific machine? ansible.cfg
- How do I specify which machine to install the ELK server on versus which to install Filebeat on? List the ELK IP 10.0.1.4 under [elk] in the ansible playbook
- Which URL do you navigate to in order to check that the ELK server is running? http://10.0.0.8:5601
