# Mamadou-Telly-Diallo-C.S
bootcamp ELK stack project1
Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

<img width="820" alt="Screen Shot 2022-05-24 at 6 55 03 PM" src="https://user-images.githubusercontent.com/99167017/170156787-2a6062a1-5f44-4398-949b-d44de0cd6bd5.png">

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yaml_files file may be used to install only certain pieces of it, such as Filebeat.

yml-files

This document contains the following details:

 .Description of the Topology
 .Access Policies
 .ELK Configuration
  Beats in Use
  Machines Being Monitored
 . How to Use the Ansible Build
Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA Web Application.

 .Load balancing ensures that the application will be highly responsive, and to restrict connections to the network.

 .The advantage of a Jumpbox is to restrict access and act as a gateway for ssh connections in the live environment.
Integrating an ELK server allow users to monitor the vulnerable VMs for changes to the CPU and system Logs.

 .Filebeat is used for collecting log events of the server thats installed on._
 .MetricBeat Collects Operation System Metrics such as CPU load, Network Traffic and other related fields.
 
The configuration details of each machine may be found below.

| Name	|Function	|IP Address|	Operating System |
| ------|---------|----------|-------------------|
|JumpBox| Gateway |10.1.0.4  |  Linux            |
| WEB1 | webserver1 |	10.1.0.5	| Linux |
| WEB2 | webserver2 |	10.1.0.6	| Linux |
| ELK	| ELK STACK	| 10.0.0.4 | Linux |

Access Policies

 The machines on the internal network are not exposed to the public Internet.

 Only the Load Balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

 .Port 80 (TCP over HTTP)
 
Machines within the network can only be accessed by Ansible Container via the JumpBox using Port 22.

 .Jump Box IP 10.1.0.4
 
A summary of the access policies in place can be found in the table below.

|Name	|Publicly Accessible	|Allowed IP Addresses|
| ----|---------------------|--------------------|
|Jump Box|	NO|	10.1.0.4|
|WEB1	|YES	|10.1.0.5|
|WEB2	|YES	|10.1.0.6|
|ELK|	NO	|10.0.0.4|

Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

 .the advantage of automating configurations with Ansible is efficint synchronicity in deployment across all systems
 
The playbook implements the following tasks:

  .Checks and installs Docker.io
 
  .Checks and installs Python3-pip
 
  .Checks and installs Docker Module (python)
 
  .Checks and downloads, and run elk container with published ports
 
  .Enable docker service on boot
 
 .Increase virtual memory
 
The following screenshot displays the result of running docker ps after successfully configuring the ELK instance
<img width="1232" alt="Screen Shot 2022-05-23 at 8 42 40 PM" src="https://user-images.githubusercontent.com/99167017/170157623-d4070308-e76a-4697-a586-905210c4a6d2.png">
Target Machines & Beats

This ELK server is configured to monitor the following machines:

|Name|	Allowed IP Addresses |
|--- |------|
|WEB1|	10.1.0.5 |
|WEB2	|10.1.0.6|

We have installed the following Beats on these machines:

 .Filebeat
 .Metricbeat
 
These Beats allow us to collect the following information from each machine:

 .Filebeat collects log files and system logs
 .Metricbeat collects metric for CPU Network and other related services
 
Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

configELK.yml is the ansible-playbook copied from install-elk.yml

curl https://columbia.bootcampcontent.com/columbia-bootcamp/CU-VIRT-CYBER-PT-02-2022-U-LOL/-/raw/main/13-ELK-Stack-Project/Activities/Stu_Day_1/Unsolved/Resources/install-elk.yml > configELK.yml

Updated the hosts file to include the ELK-VM under the category elk

nano /etc/ansible/hosts add [elk] and 10.0.0.4

Run the playbook, and navigate to 20.242.81.178:5601 to check that the installation worked as expected.

On CLI local host (if unix-based) open 20.242.81.178:5601

As a Bonus, provide the specific commands the user will need to run to download the playbook, update the files, etc.
