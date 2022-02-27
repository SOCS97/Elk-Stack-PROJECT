## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

 /images/network.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  /etc/ansible/install-elk-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly safe and secure, in addition to restricting traffic to the network.

- What aspect of security do load balancers protect? What is the advantage of a jump box? 

  Load balancers protect against Distributed Denial-of-Service (DDoS) attacks.

  Jump boxes are secure computers that administrators connect first before connecting to possible untrustworthy networks.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the metrics and system logs.

- What does Filebeat watch for?

  Filebeat watches for logs and files

- What does Metricbeat record?

  Metricbeat records host metrics

The configuration details of each machine may be found below.

| Name               | Function   | IP Address | Operating System    |
|--------------------|------------|------------|---------------------|
| JumpBoxProvisioner | Gateway    | 10.0.0.4   | Linux Ubuntu Server |
| Web-1              | Server     | 10.0.0.7   | Linux Ubuntu Server |
| Web-2              | Server     | 10.0.0.8   | Linux Ubuntu Server |
| Web-3              | Server     | 10.0.0.9   | Linux Ubuntu Server |
| Elk-Net            | Elk Server | 10.2.0.0   | Linux Ubuntu Server |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- Personal Public IP Address

Machines within the network can only be accessed by the JumpBoxProvisioner.

- Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name               | Publicly Accessible | Allowed IP Addresses |
|--------------------|---------------------|----------------------|
| JumpBoxProvisioner | No                  | Personal Public IP   |
| Web-1              | No                  | 10.0.0.4             |
| Web-2              | No                  | 10.0.0.4             |
| Web-3              | No                  | 10.0.0.4             |
| Elk-Net            | Yes                 | Personal Public IP   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- What is the main advantage of automating configuration with Ansible?

  YML Playbooks is the main advantage.

The playbook implements the following tasks:

- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

  - SSH (Secure Shell) into the JumpBoxProvisioner
  - View your list of docker containers (sudo docker container list -a)
  - Start docker (sudo docker start *insert unique name*)
  - Attach docker (sudo docker attach *insert unique name*)
  - Go to /etc/ansible/roles and create the ELK playbook
  - Run the ELK playbook

### Target Machines & Beats

This ELK server is configured to monitor the following machines:

- List the IP addresses of the machines you are monitoring_

  Web-1
  Web-2
  Web-3

We have installed the following Beats on these machines:

 Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:

 As stated earlier, Filebeat watches for logs and files. Metricbeat records host metrics.

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat Config file to /etc/ansible/files.
- Update the /etc/ansible/host file to include the private server IP addresses.
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.

Answer the following questions to fill in the blanks:

-Which file is the playbook?
 
 filebeat-playbook.yml

-Where do you copy it?

 /etc/ansible/roles

-Which file do you update to make Ansible run the playbook on a specific machine?

 hosts

-How do I specify which machine to install the ELK server on versus which to install Filebeat on?

 In the "hosts" file

-Which URL do you navigate to in order to check that the ELK server is running?

 http://[your.VM.IP]:5601/app/kibana
