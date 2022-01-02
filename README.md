## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Network Diagram (Homework 12.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Network Diagram file may be used to install only certain pieces of it, such as Filebeat.

  -Filebeat Installer (filebeatinstall.txt)
  -Metricbeat Installer (Metricbeat.txt)
  -Elk Setup (elksetupyaml.txt)

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

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the docker containers and system logs.


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.9   | Linux            |
| Web1     | Webserver| 10.0.0.10  | Linux            |
| Web2     | Webserver| 10.0.0.11  | Linux            |
| Elk      | Elk Stack| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 98.53.184.101

Machines within the network can only be accessed by the Jumpbox.
-The Elk machine is only accesable through my workstation 98.53.184.101

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 98.53.184.101        |
| Elk      | No                  | 98.53.184.101        |
| Web1/2   | No                  | 10.0.0.9             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
It creates a playbook that can be run on any computer with little editing required.

The playbook implements the following tasks:
It installs python3-pip and uses it to install Docker
It allows more memory to be allocated for docker
It downloads and launches the docker elk container
It enables the docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Docker ps.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.10
10.0.0.11

We have installed the following Beats on these machines:
filebeat
metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat collects information from the system logs while metricbeat collects metrics an statistics, all of the collected data is then displayed in Kibana for easy analysis.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elksetupyaml.txt file to your jumpbox.
- Update the elksetupyaml.txt file to be a .yml file and to include the proper hosts and user
- Run the playbook, and navigate to http://(ELK IP):5601/app/kibana#/home/ to check that the installation worked as expected.


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
curl -LO https://github.com/Danny4rest/Project-Files/blob/04d4e0fe792efbca83fbe72f01c2b9bc7d29f0b1/elksetupyaml.txt
mv elksetupyaml.txt elksetupyaml.yml
nano elksetupyaml.yml
ansible-playbook ./elksetupyaml.yml
