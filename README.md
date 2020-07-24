## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Images/Azure Network Layout.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible playbook file may be used to install only certain pieces of it, such as Filebeat.

  Elk-server-yml.txt

This document contains the following details:
- Description of the Topology 
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly responsive, in addition to restricting access to the network.
	As such the load balancers are great from protecting the accessibility of your network by controlling the flow of traffic.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the server activity and system integrity.
File beat monitors select log files.
Metric beat monitors metrics form the OS and services that run on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name         | Ip Address     | Function   | Os     |
|--------------|----------------|------------|--------|
| Red Team     | 168.62.206.127 | Jump Box   | Ubuntu |
| DVWA-VM1     | 137.135.25.160 | Target 1   | Ubuntu |
| DVWA-VM2     | 127.135.0.113  | Target 2   | Ubuntu |
| ELK-Stack VM | 13.90.155.173  | Elk server | Ubuntu |




### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
68.43.109.117

Machines within the network can only be accessed by SSH.
I allowed the red team VM to access the network = IP. 168.62.206.127

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses                         
|------------|---------------------|-------------------------------------
| Red Team   | Yes                 | 68.43.109.117                                 
| dwvma-vm1  | No                  | 168.62.206.127, 13.90.155.173                 
| dwvma-vm2  | No                  | 168.62.206.127, 13.90.155.173                 
| Elk-Server | No                  | 168.62.206.127, 137.135.25.160,      
                                     137.135.0.113 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it is highly reusable.  The playbook that was written had the ability to be reused to set up any other machine.

The playbook implements the following tasks:
* Installs docker python module
* Increases the vitual memory dedicated to the vm
* Downloads and launches an ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/Elk-Container.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
137.135.25.160, 137.135.0.113

We have installed the following Beats on these machines:
* Metricbeat
* Filebeat
* Packetbeat

These Beats allow us to collect the following information from each machine:
* Filebeat keeps track of log files on the machines.
* Metricbeat keeps track of the metrics running on the os and system applications.
* Packetbeat analyzes the network packets.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elkserver-yml file to the ansible folder.
- Update the ansible hosts file to include the desired ip of the machine as well as the group you want it to be a part of.
- Run the playbook, and navigate to https://13.90.155.173/ to check that the installation worked as expected.





