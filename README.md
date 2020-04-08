# Ansible_DD
In this repo, we'll try to DD (dive deep) into Ansible aspect.

# Our infrastructure

In our case we will two machines:
- An ansible host: Fedora Workstation 31
- A device target (on the same network): Ubuntu 16.04 LTS. The target host requires upstream internet access. 

# Pre-requisites

In order to let Ansible work, the OS must have a python interpreter installed. In fact, Ansible maintains a single code base that runs on both Python 2 and Python 3 (Python 2.7 or later is recommended).  