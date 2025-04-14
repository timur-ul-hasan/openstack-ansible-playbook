ansible-playbook -i inventory.ini setup_openstack.yml

.
├── Documentation.md
├── Readme.md
├── host_vars
│   └── vagrant.yml
├── inventory.ini
├── setup_openstack.yml
├── tasks
│   ├── base_setup.yml
│   ├── ceilometer.yml
│   ├── horizon.yml
│   ├── keystone.yml
│   ├── neutron.yml
│   ├── nova.yml
│   ├── swift.yml
│   └── trove.yml
└── vars
    ├── global.yml
    └── secrets.yml