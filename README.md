# BootcampProject1 

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


