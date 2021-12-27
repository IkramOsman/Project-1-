## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK Diagram](https://github.com/IkramOsman/Project-1-/blob/main/Diagrams/Untitled%20Diagram.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - [Ansible Playbook](https://github.com/IkramOsman/Project-1-/tree/main/Ansible)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly Secure_____, in addition to restricting public access to the network.
- _TODO: What aspect of security do load balancers protect? web traffic in and out of the of the network What is the advantage of a jump box? gateway into the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _networks?____ and system _logs____.
- What does Filebeat watch for?_Watches system log data through events. 
- What does Metricbeat record?_Collects metrics and sends those metrics to specified output.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  |10.0.0.4    | Linux            |
| ElkServer|  Kibana  |10.1.0.4    | Linux            |
| WEB 1    |  DVWA    |10.0.0.5    | Linux            |
| WEB 2    |  DVWA    |10.0.0.6    | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the host__ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Add whitelisted IP addresses_ Jumpbox 10.0.0.4, ELK Virtual Machine 10.1.0.4, Web 1 10.0.0.5, Web 2 10.0.0.6

Machines within the network can only be accessed by _Docker Container____.
- Which machine did you allow to access your ELK VM? Jumpbox Machine What was its IP address?_10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses           |
|----------|---------------------|----------------------          |
|Jump Box  |     No              | 10.0.0.5, 10.0.0.6,10.1.0.4    |
|ELK       |     No              |     10.0.0.4                   |
|Firewall  |     No              |   10.0.0.4, 10.1.0.4            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?_It allows different systems to communicate through related configuration using yaml. 

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Use apt module to install docker.io, 
- use apt module to install pip3, 
- use pip module to install docker python module, 
- use system control module to use more memory
- use docker_container module to download and launch a docker elk container & use systemd module to enable service docker on boot. 


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker PS output-Screenshot](https://raw.githubusercontent.com/IkramOsman/Project-1-/main/Docker%20PS%20Output%20.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines: Web 1 and Web 2 
- List the IP addresses of the machines you are monitoring_ 10.0.0.5, 10.0.0.6

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed_ metricbeat and filebeat

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
- Metricbeat: collects data to be sent to the specified location for example to logstash. ie: When I'm working on web 1, it records my changes communicates that to output. 
- Filebeat: collects data of log events. ie: I expect it to centralize my log data. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _YAML____ file to  Ansible file_____.
- Update the _Ansible____ file to include playbook
- Run the playbook, and navigate to IP address_ to check that the installation worked as expected.

_ Answer the following questions to fill in the blanks:_
- Which file is the playbook? there are multiple files, the elk file. Where do you copy it?_first step install-elk.yml by running the command and than copied it to a blank nano. 
- Which file do you update to make Ansible run the playbook on a specific machine? Update the host file. How do I specify which machine to install the ELK server on versus which to install Filebeat on?_Changed the host IP address to the ELK IP address to ensure the playbook downloaded to the correct machine on lines 1105 and 1805 on the filebeat configuration. 
- _Which URL do you navigate to in order to check that the ELK server is running? http://40.122.32.177/5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._