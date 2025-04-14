Setup Openstack Server:-
- Requirements:
  - Python 3.10 or higher
  - Ansible
  - SSH access to the server

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

4.
ansible-playbook -i inventory.ini setup_openstack.yml