# Setup Openstack Server:-
Following are the recommended hardware specifications for each node:
## Controller Node
● CPU: Minimum 4 cores

● RAM: Minimum 8 GB

● Storage: Minimum 100 GB

● Network: 1 NIC for management, 1 NIC for external access

## Compute Node
● CPU: Minimum 4 cores

● RAM: Minimum 16 GB

● Storage: Minimum 100 GB

● Network: 1 NIC for management, 1 NIC for external access


## Server Setup


### BIOS and Firmware Configuration
Before installing the OS, configure BIOS/UEFI for virtualization (Intel VT-x/AMD-V), set boot order, disable unnecessary hardware, and after reboot, disable swap for OpenStack services:
```bash
sudo swapoff -a && sudo sed -i '/ swap / s/^/#/' /etc/fstab
```

### Software Requirements:

● Operating System: Ubuntu 22.04 LTS

● OpenStack Release: Train or later

● Ansible: Version 2.9 or later

● Python: Version 3.6 or later


## Ansible Playbook for OpenStack Setup 

## Client Setup

### Software Requirements

● OpenStack Release: Train or later

● Ansible: Version 2.9 or later

● Python: Version 3.6 or later


- Steps:

1. Make sure you have Python 3.10 or higher installed on your system.

2. Create a virtual environment (optional but recommended):
```bash
python3 -m venv openstack_env
source openstack_env/bin/activate
```
3. Install Ansible:
```bash
pip install ansible
```
4. Clone the repository:


### Run for the Vagrant VM:
```bash
ansible-playbook -i inventory.ini setup_openstack.yml
```

### For password based authentication, you can use the `--ask-pass` option (Not recommended for production).

```bash
ansible-playbook -i inventory.ini setup_openstack.yml --ask-pass --ask-become-pass
```

### For SSH key based authentication, you can use the `--private-key` option.

```bash
ansible-playbook -i inventory.ini setup_openstack.yml --private-key /path/to/your/private/key
```