# Ansible_DD
In this repo, we'll try to DD (dive deep) into Ansible aspect.

# Our infrastructure

In our case we will many machines:
- An ansible host (primary host) on a virtual machine running Fedora Workstation 31 with:
    - Last version of Ansible installed
    - Python netaddr package installed: gives us the the ability to manipulate and modify the IP address. 
    - We'll use a dynamic inventory module (through packet-python with the packet_net.py dynamic inventory script)
    - The ansible tower (AWX project) will be installed: it will give a graphical management environment. 

- 4 devices targets (on the same network): 4 virtual machines running Ubuntu 16.04 LTS. The target host requires upstream internet access (and we have to know its IP address) and: 
    - Python 2.7 or later installed
    - Pip installed (sudo apt install python-pip)
    - Netaddr installed (sudo apt install python-netaddr)

- A single virtual host (Ubuntu 16.04) running: 
    - A VyOS virtual router: it will be a network device management 
    - We'll also run Ansible on that machine directly (only have ansible on the primary host talk to Ansible through the routers isn't a possible configuration)

Both of them will be created through VM machines. 

# Pre-requisites

In order to let Ansible work, the OS must have a python interpreter installed. In fact, Ansible maintains a single code base that runs on both Python 2 and Python 3 (Python 2.7 or later is recommended). 

# Creation of the Infrastructure 

In order to create our 4 VMs quickly, we'll use Vagrant. 
- Document the installation of Vagrant (on the Mac) 

# Next 

## Defining task execution with host groups 

- Try to create the 4 VMs with Vagrant 
- Try to connect through SSH with the mac to the ubuntu VMs
- Transfer the video from Windows to Mac
- Document the task.yml and put a link to the file module on Ansible 
- Detail the dynamic variable "file_state"