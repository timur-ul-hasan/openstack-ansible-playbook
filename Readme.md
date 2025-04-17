# Setup Openstack Server & Client

## Prerequisites

Following are the recommended hardware specifications for each node:

### Controller Node

● CPU: Minimum 4 cores

● RAM: Minimum 8 GB

● Storage: Minimum 100 GB

● Network: 1 NIC for management, 1 NIC for external access

### Compute Node

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

### Operating System Installation

1. Install Ubuntu 22.04 LTS on the controller and compute nodes.

2. Make sure to select the following options during installation:
   - OpenSSH server
   - Standard system utilities
   - Minimal installation (optional)
3. Configure network interfaces:
    - Controller Node: Assign a static IP address for management and external access.
    - Compute Node: Assign a static IP address for management and external access.

4. Set up hostname resolution:
   - Edit `/etc/hosts` to include the IP addresses and hostname of the controller and compute nodes.

5. Disable the firewall (optional for testing):

```bash
sudo ufw disable
```

6. Ensure the system is updated:

```bash
sudo apt update && sudo apt upgrade -y
```

## Client Setup

## Ansible Playbook for OpenStack Setup 
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
```bash
git clone <repository-url>
```
5. Navigate to the cloned directory:
```bash
cd openstack-playbook
```
6. Install required Ansible collections:
```bash
ansible-galaxy collection install -r requirements.yml
```
7. Install required Ansible roles:
```bash
ansible-galaxy install -r requirements.yml
```
8. Create an inventory file (`inventory.ini`) with the following content:
```ini
[controller]
controller ansible_host=<controller_ip> ansible_user=<ssh_user>
[compute]




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