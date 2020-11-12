## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK Server](ELK/Diagrams/ELKNetwork.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat or Metricbeatr.

  - [ELK Install File](ELK/YAMLFiles/install-elk.yml) 
  - [Filebeat Install](ELK/YAMLFiles/filebeat-playbook.yml) 
  - [Metricbeat Install](ELK/YAMLFiles/metricbeat-playbook.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
- Load balancers ensures availability and reliability of the servers. 

What is the advantage of a jump box? 
- A jump box is a secure computer that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- _ What does Filebeat watch for? Filebeat watches for log files/locations and collects log events._
- _ What does Metricbeat record? Metricbeat records metric and statistical data from the opertaing system and from services running on the server._

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                 | Function | IP Address | Operating System |
|----------------------|----------|------------|------------------|
| Jump-Box-Provisioner | Gateway  | 10.0.0.4   | Linux (ubuntu)   |
| Web-1.1              | Server   | 10.0.0.8   | Linux (ubuntu)   |
| Web-2.1              | Server   | 10.0.0.9   | Linux (ubuntu)   |
| ELK-VM               | Server   | 10.1.0.4   | Linux (ubuntu)   |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine and the ELK-VM can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Personal IP Address
- Jumpbox to ELK-VM via 10.0.0.4

Machines within the network can only be accessed by SSH.
- The Elk-VM (10.1.0.4) differs because it can be accessed via the Jumpbox (10.0.0.4) or the Personal IP.

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses   |
|----------------------|---------------------|------------------------|
| Jump-Box-Provisioner | No                  | Personal IP            |
| Web-1.1              | No                  | 10.0.0.4               |
| Web-2.1              | No                  | 10.0.0.4               |
| ELK-VM               | No                  | 10.0.0.4 & Personal IP |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because:
- Ease of use with minimal learning curve
- Allows for Playbooks to configure multiple machines through a single command

The playbook implements the following tasks:
- Create a new VM and keep note of the Private and Public IP.
  - The Private IP will be used for SSHing into the box and the Public IP will used to monitor metrics via Kibana Portal
- Download and configure the "elk-docker" container
  - Update the hosts.conf to add your new VM server and Private IP
  - Then create a new Playbook to download, install, configure your new server, and start the container (Reference: [ELK Install File](ELK/YAMLFiles/install-elk.yml))
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker ps](ELK/Ansible/Container.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
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
