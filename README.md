# Network-w-ELK-Stack Deployment

The files in this repository were used to configure the network depicted below.

To make grading easier I've linked the required screenshots here (I'll delete them after the projects graded)
 
 [Red-NSG](https://github.com/danemd/Network-w-ELK-Stack/blob/screenshots/nsg_red.png)
 
 [ELK-NSG](https://github.com/danemd/Network-w-ELK-Stack/blob/screenshots/nsg_ELK.png)
 
 [VM's](https://github.com/danemd/Network-w-ELK-Stack/blob/screenshots/VMs.png)
 
 [Topology](https://github.com/danemd/Network-w-ELK-Stack/blob/screenshots/topology.png)
 
 [Peering](https://github.com/danemd/Network-w-ELK-Stack/blob/screenshots/red-ELK_peering.png)
 
[TODO: Update the path with the name of your diagram](Images/diagram_filename.png) 

![Network Diagram](https://github.com/danemd/Network-w-ELK-Stack/blob/Network-Diagram/Network%20W_%20ELK%20Stack%20(1).jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  [Elk Install](https://github.com/danemd/Network-w-ELK-Stack/blob/YAML/ELK-Install.yml)
  
  [Filebeat Install](https://github.com/danemd/Network-w-ELK-Stack/blob/screenshots/filebeat-playbook.yml)
  
  [Metricbeat Install](https://github.com/danemd/Network-w-ELK-Stack/blob/screenshots/metricbeat-playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

# Load balancing ensures that the application will be highly resilient to network load and potential DDos attacks, in addition to restricting unauthorized access to the network.

# The load balancer serves the purpose of maintaining access to the application regardless of if one of the web servers goes down. In such an event the loadbalancer redirects to the application via a working web server. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the changes to the log files and system metrics.
# Filebeat monitors for alteration of log files and triggers an alert. #
# Metricbeat records system metrics for observation via the Elastic server. #

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.7, 13.82.87.141   | Linux            |
| Web-1    | Access to App   | 10.0.0.4   | Linux           |
| Web-2    | Access to App  | 10.0.0.5   | Linux            |
| Web-3    | Access to App  | 10.0.0.6   | Linux            |
| Load Balancer    | App Persistence      | 13.68.199.33 | Linux |
| ELK Stack| Monitor App   | 10.1.0.4, 20.55.207.145   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
# Jump-Box: 24.98.14.87

Machines within the network can only be accessed by the Jump-Box-Provisioner machine.
# Jump-Box-Provisioner: 13.82.87.141

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                  | 24.98.14.87         |
| Web-1    | No                  | 10.0.0.7             |
| Web-2    | No                  | 10.0.0.7             |
| Web-3    | No                  | 10.0.0.7             |
| ELK Stack| No                  | 10.0.0.7             |
| Load Balancer    | No                | All                 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
# Ansible allows the automated download of the ELK stack, beats, and configuration onto the ELK server and Web Machines via YAML files. #

The playbook implements the following tasks:
- Install Docker.io
- Install python3-pip
- Install Docker Module
- Increase Virtual Memory
- Download and Launch Docker ELK Container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker ps](https://github.com/danemd/Network-w-ELK-Stack/blob/screenshots/elk_docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
# 10.0.0.4, 10.0.0.5, 10.0.0.6 #

We have installed the following Beats on these achines:
# Filebeat and Metricbeat # 

These Beats allow us to collect the following information from each machine:
# Filebeat monitors and gathers log files, inspecting them for changes. For instance if the system.log is altered Filebeat will trigger an alert. 
# Metricbeat monitors and collects system data. This can be useful for returning the status of your system's OS and ensuring it is successfully running. 

### Using the Playbook ###
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
# Copy the public key file to the host machine. #
# Update the hosts file to include the hosts' IPs that the playbook will configure. #
# Run the playbook, and navigate to the target machine to check that the installation worked as expected. #

# The YAML file is the playbook and it is copied to /etc/ansible/roles/<YAML-file.yml> #

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_

# To specify a particular machine to update via the playbook files, navigate to the hosts file within the Ansible container within the Jump-Box-Provisioner machine. You may establish a new group within the hosts file that YAML files may be run on. However, once a new group is created, you will need to point to it within the desired YAML playbook file. For instance if you create a new hosts group called "Test-1" that you wish to install the ELK server on, navigate to the ELK-install.yml file and open the editor. Then modify the hosts it points to to include the "Test-1" group. #
- _Which URL do you navigate to in order to check that the ELK server is running?
# http://20.55.207.145:5601/app/kibana #

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
# ansible-playbook /etc/ansible/roles/filebeat-install.yml #
# ansible-playbook /etc/ansible/roles/ELK-install.yml #
# ansible-playbook /etc/ansible/roles/my-first-playbook.yml #
