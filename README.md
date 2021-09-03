# BootcampProject1 

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


/BootcampProject1/Diagrams/topology.png



These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

/etc/ansible/install-elk.yml
(to view in the repo)/BootcampProject1/Ansible/install-elk.yml


This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible/available, in addition to restricting unauthorized access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_ DDos attacks - advantage is to give user or customers access to your servers on nodes that are secured and monitored. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_ log events in the server file system.
- _TODO: What does Metricbeat record?_ metric logs and statistics 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  |10.0.04     | Linux            |
| Web -1   |web server| 10.0.0.7   | Linux            |
| Web -2   |web server|  10.0.0.8  | Linux            |
| Load Bal |distribute|40.88.48.149| Linux            |
| ElkVM    |server    |52.156.96.13| Linux 		     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _ELK__ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Web 1 and Web 2 10.0.0.7   10.0.0.8

Machines within the network can only be accessed by JumpBox.
- The ip address is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | yes                 | (My Ip address       |
| Web 1    |   no                | 10.0.0.7             |
| Web 2    |    no               | 10.0.0.8             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? The Playbook saves time if you need to complete this task for 100+ machines. Automation minimizes the potential for errors compared to doing everything manual.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- installs docker.io and downloads the file image
- downloads and installs the script language python pip3 module
-install docker
-the playbook then installs the ELK contain
-enables the docker application

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance. 

(view screenshot on the repo)/BootcampProject1/Diagrams/Elk ps.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.7 10.0.0.8

We have installed the following Beats on these machines:
- Filebeat and metricbeat

These Beats allow us to collect the following information from each machine:
-log files Filebeat is a lightweight shipper for logs
-Auditbeat lightweight shipper for audit data
-Metric beat is collecting you metric logs 
-Winlogbeat lightweight shipper for windows event logs


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the __configuration___ file to _ansible roles playbook.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ Configuration file and copy it to  ansible files where you would copy for the yml playbook

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? edit the host file in order to add the webserver ip address ansible_python_interpreter=/usr/bin/python3

- _Which URL do you navigate to in order to check that the ELK server is running? http://52.156.96.13:5601 (kibana landing page)

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
ansible-playbook [Name of yml] and filebeat-playbook.yml [Name of file]


Creating an Azure cloud can be easy as 1, 2, 3.

When setting up virtual networks we must keep in mind they must all incorporate complex architecture, be manageable, and readily available.
These features have given the cloud a leg up when it comes to its effectiveness as a tool/service in the industry. 

In order to begin this project, one must understand how each connection is being accomplished on the cloud.
We must understand that creating a virtual network there has to be a resource group that we can somehow build our virtual network on. In this case the virtual network will be built on the Azure. In Azure Resource groups can allow different resources on our virtual network to set up the virtual computers, firewalls, and other resources needed to set up our environment. This is why I created the resource group first to lay the groundwork for the virtual machine. The Resource I created was placed in the East cost with the option to select the most cost efficient virtual machine to attach to that resource group. 

Now that we have a resource group we can add a virtual network to the resource group. The virtual network is important to build because it allows us to build the framework in which our virtual machines will use to communicate with each other and exchange data.  For this project an IPv4 address was assigned in Azure coupled with subnets. The Vnet enables many types of Azure resources such as the virtual machines to communicate with each other, other on premises servers and the outside internet. For this project I left the security settings as is on the azure platform with DDoS protection standard disabled, Firewall disabled, and the bastion host disabled. 

Now that we have the resource group and virtual network set up, it is necessary to create the security groups. At this point my goal is to have my network running with a firewall attached to the cloud. The fire wall is important to cloud security because we can block or allow traffic to our liking by setting security rules. A network security group will be used to block/allow traffic to our virtual network and the machines that will be deployed on the virtual network. To do this we will create the network security group by adding it to the resource group we created and creating inbound rules for the security group to decide which connections we will allow to go into and from the connections we created for the virtual network. 

Next we must create the virtual machines where virtual computing will be completed. Virtual computers will need to have the correct RAM based on what kind of things you want to be completed on the virtual machines. Coupled with the correct Storage, CPU, and Disks to store all the data on each network. All of this depends on the demand of the project or whatever you are trying to accomplish with this cloud machine.

For this project I created a Jump box provisioner that will allow us to ssh into our virtual machines. This was done by clicking the "create a virtual machine" button to which I selected the regions and the virtual machine availability zone.  The availability option and the size of the machine must be set based on the appropriate GiB memory for what we arer trying to accomplish. 

After we have set the ground work in Azure for the Jumpbox virtual machine we can create the SSH keys on our local machines which will be used to create the ssh keys that will be necessary to connect our connections and our virtual machine.  this is done on the command line by running <ssh-keygen> if it has not already been done already. SSH connections are somewhat weak encryptions and can easily be brute forced so it is important to keep this information on the admin level. 
When we run the <ssh-keygen> command on the command line it will create a directory in the ~/.ssh/id_rsa folder. we can now use the public key that ws generated and go back into azure to create a username and paste the existing public key in the space available. 


