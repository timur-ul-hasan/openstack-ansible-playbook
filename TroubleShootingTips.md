# Troubleshooting Tips


## 1. Check the Internet Connection for the Server System

Sometimes, the server system may not have a proper internet connection, wrong DNS settings, or firewall rules that block access to the internet. 


## 2. Network configuration

Neutron network configuration is crucial for OpenStack to function properly. Ensure that the network settings are correct and that the necessary services are running. You can check the status of Neutron services using the following command:

```bash
openstack network agent list
```

