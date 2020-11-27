# Wazuh Open Source Security Platform

- Note: Information is taken from the website below:

Wazuh is a free, open source and enterprise-ready security monitoring solution for threat detection, integrity monitoring, incident response and compliance.

This process is simple and easy to setup. All we have to do is import the **.ova** file into our Hypervisor and run the system.

- Virtual Appliance:
- https://packages.wazuh.com/4.x/vm/wazuh-4.0.2_1.11.0.ova

~~~
System Components:

CentOS 7
Wazuh manager: 4.0.2
Open Distro for Elasticsearch: 7.9.1
Filebeat-OSS: 7.9.1
Kibana: 7.9.1
Wazuh Kibana plugin: 4.0.2-7.9.1
~~~

- First, import the OVA in the virtualization platform and run the virtual machine. The user root password is wazuh and the username/password for the Wazuh API is wazuh-wui/wazuh-wui.

Note: You will need to login into the system and get the IP address from the server.

By default the type of the network interface is bridge. The VM will try to get an IP address from the network’s DHCP server. Alternatively, a static IP address can be set by configuring the proper network files on the CentOS operating system that the virtual machine is based on.
~~~
To access the web interface:

URL: https://<wazuh_server_ip>
user: admin
password: admin
~~~



### The following video explains how to import and run the virtual machine.:
- https://www.youtube.com/watch?v=uijZuneDPPk