# Network-w-ELK-Stack Deployment

The files in this repository were used to configure the network depicted below.

[TODO: Update the path with the name of your diagram](Images/diagram_filename.png) https://app.diagrams.net/#G1mUlqHjCbLol0Bw6R1KyVzTstcozPsN4y

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._  *Do I need to make an all encompassing YAML file for this? 

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

# Load balancing ensures that the application will be highly resilient to network load and potential DDos attacks, in addition to restricting unauthorized access to the network.
~~- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_~~ 
# The load balancer serves the purpose of maintaining access to the application regardless of if one of the web servers goes down. In such an event the loadbalancer redirects to the application via a working web server. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
~~- _TODO: What does Filebeat watch for?_~~ 
# Filebeat monitors log files for suspicious behavior and forwards the to the Elastic server.        *Is it via Elastic or Kibana?
~~- _TODO: What does Metricbeat record?_~~ 
# Metricbeat records system metrics and records for observation via the Elastic server. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.7   | Linux            |
| Web-1    | Access to App   | 10.0.0.4   | Linux           |
| Web-2    | Access to App  | 10.0.0.5   | Linux            |
| Web-3    | Access to App  | 10.0.0.6   | Linux            |
| Load Balancer    | App Persistence      | 13.68.199.33 | Linux |
| ELK Stack|          | 10.1.0.4, 20.55.207.145   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by the Jump-Box-Provisioner machine.
~~- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_~~ 
# Jump-Box-Provisioner: 13.82.87.141

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 24.98.14.87          |     *Should I have my personal IP here?*
| Web-1    | No                  | 10.0.0.7             |
| Web-2    | No                  | 10.0.0.7             |
| Web-3    | No                  | 10.0.0.7             |
| ELK Stack| No                  | 10.0.0.7             |
| Load Balancer    | Yes                 | All                  |     *Is it the load balancer or the Application itself that's publicly accessable?* 
|          |                     |                      |     *Should Kibana be listed?*

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
~~- _TODO: What is the main advantage of automating configuration with Ansible?_~~
# Ansible allows the automated download of the ELK stack, beats, and configuration onto the ELK server and Web Machines via YAML files. #

The playbook implements the following tasks:
~~- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._~~
- Install Docker.io
- Install python3-pip
- Install Docker Module
- Increase Virtual Memory
- Download and Launch Docker ELK Container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)
C:\Users\dane6\Pictures\Screenshots

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
#10.0.0.4, 10.0.0.5, 10.0.0.6

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
#Filebeat and Metricbeat 

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

