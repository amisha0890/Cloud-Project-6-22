## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

./Diagrams/XCorp_Network_Architechture_with_ELK.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the docker_config_playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - Ansible/docker_config_playbook.yml
  - ./Ansible/filebeat-playbook.yml
  - ./Ansible/metricbeat-playbook.yml
  - ./Ansible/install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- What aspect of security do load balancers protect? A load balancer is crucial for an organization in the event of a DDoS attack. It will shift attack traffic seamlessly to another. A load balancer also distributes traffic evenly to enhance user experience.   
- What is the advantage of a jump box? A jump box is advantageous in that it gives a single secure origin access point to the user. From this jumpbox then can users access servers. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jump box and system network.
- What does Filebeat watch for? FIlebeat monitors log files from specific locations.
- What does Metricbeat record? Metricbeat collects system data from servers.

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |
|----------|---------- |------------|------------------|
| Jump Box | Gateway   | 10.0.0.1   | Linux            |
| Web-1    | Webserver | 10.0.0.5   | Linux            |
| Web-2    | Webserver | 10.0.0.6   | Linux            |
| ELK      | Data      | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 66.76.216.128

Machines within the network can only be accessed by the Jump Box.
- The Jump Box Provisioner with IP 168.62.194.60 is the only machine allowed to access the ELK VM.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses  |
|----------|---------------------|---------------------- |
| Jump Box | No                  | 66.76.216.128         |
| Web-1    | No                  | 10.0.0.4/10.1.0.4     |
| Web-2    | No                  | 10.0.0.4/10.1.0.4     |
| ELK      | No                  | 10.0.0.4              
			  
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? It allows you to configure multiple servers at once and from a security perspective if a playbook is ran on a control machine then all the virtual machines will be updated with the same details. Each Machine will no longer need to be monitored for security compliance.

The playbook implements the following tasks:
- The steps of the ELK installation play.
- Install docker.io
- Install pip3
- Install Docker python module
- Increase virtual memory
- Download and launch Docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
/reimagined-happiness/Images/docker_ps_output.png


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| Name  	| IP Address 	|   	|   	|   	|
|-------	|------------	|---	|---	|---	|
| Web-1 	| 10.0.0.5   	|   	|   	|   	|
| Web-2 	| 10.0.0.5   	|   	|   	|   	|
|       	|            	|   	|   	|   	|

We have installed the following Beats on these machines:
- FIleBeat and MetricBeat

These Beats allow us to collect the following information from each machine:
- FileBeat- collects file system data such as log events.
- MetricBeat- collects system metrics such as runtime

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to Ansible Control Node.
- Update the hosts file to include webserver and ELK
- Run the playbook, and navigate to Kibansa to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running? You will go to http://20.84.67.67:5601/app/kibana where the IP is the ELK server public IP.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
