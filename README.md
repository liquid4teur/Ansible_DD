# Ansible_DD
In this repo, we'll try to DD (dive deep) into Ansible aspect.

# Pre-requisites

In order to let Ansible work, the OS must have a python interpreter installed. In fact, Ansible maintains a single code base that runs on both Python 2 and Python 3 (Python 2.7 or later is recommended).

# Our infrastructure

In our case we will many machines:
- An ansible host (primary host) on a virtual machine running Ubuntu 16.04 with:
    - Last version of Ansible installed
    - Python netaddr package installed: gives us the the ability to manipulate and modify the IP address.
    - We'll use a dynamic inventory module (through packet-python with the packet_net.py dynamic inventory script)
    - The ansible tower (AWX project) will be installed: it will give a graphical management environment.
    - This host will talk to the others (4 devices target and the virtual router).

- 4 devices targets (2 web servers and 2 data bases server on the same network): 4 virtual machines running Ubuntu 16.04 LTS. The target host requires upstream internet access (and we have to know its IP address) and:
    - Python 2.7 or later installed
    - Pip installed (sudo apt install python-pip)
    - Netaddr installed (sudo apt install python-netaddr)

- A single virtual host (Ubuntu 16.04) running:
    - A VyOS virtual router: it will be a network device management
    - We'll also run Ansible on that machine directly (only have ansible on the primary host talk to Ansible through the routers isn't a possible configuration)

Both of them will be created through VM machines.

# Creation of the Infrastructure

To create our infrastructure, we'll use VirtualBox and the Linux distribution [Ubuntu 16.04 LTS](http://releases.ubuntu.com/16.04/).

# More 

I created the VMs on Hyper-V. In order to access it directly from my host machine, I installed on each Ubuntu VM **openssh-server** as a service:
>sudo apt install openssh-server

Verify that the SSH server is running:
>sudo service ssh status 

Then, you have to know the IP address of the VM on the LAN:
>hostname -I

Now, from your host machine, you can connect to the VM with the command:
>ssh login@local_ip_address

# Resources

## SSH

- [How to enable SSH on Ubuntu](https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-18-04/)
- [Know the IP address](https://doc.ubuntu-fr.org/tutoriel/connaitre_son_adresse_ip)
- [Remote access with SSH](https://formation-debian.viarezo.fr/ssh.html#idp12275120)
- [Login with SSH](https://linux.developpez.com/formation_debian/ssh.html#AEN6672)

# Further Development

## Defining task execution with host groups

- Try to create the 4 VMs with Vagrant
- Try to connect through SSH with the mac to the ubuntu VMs
- Document the task.yml and put a link to the file module on Ansible
- Detail the dynamic variable "file_state"