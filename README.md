# ELK-SIEM + Wazuh Deployment Guide

- Creating an Elasticsearch + Kibana + Wazuh SIEM 

These documents are going to show you how I setup my ELK-SIEM + Wazuh workstations. This process can take a bit to complete and some parts are just import and you are done. Now these installs are two different devices, which are similar. While very different with how you ingest data and install agents. 

-----------------------

- Note: This process was setup on a VMware ESXI 6.7.OU3B  and these machines are running 24/7. 
- Now if you wanna use that process then this setup guide is still the same.

-----------------------



I am trying to make this process simple are straight to the point. So that you can follow along and re-create the same setup that I have created.

## Resource References:

-----------------------

- What is Elasticsearch? [Docs](https://www.elastic.co/guide/en/elasticsearch/reference/current/elasticsearch-intro.html)

- What is Kibana? [Docs](https://www.elastic.co/guide/en/kibana/current/introduction.html)

- What is Wazuh? [Docs](https://documentation.wazuh.com/4.0/virtual-machine/virtual-machine.html#virtual-machine)

-----------------------

## Required Software


- Hosting Server Software 

- ubuntu Server 18.04 & 20.04 LTS [Downloads](https://ubuntu.com/download/server)

- The Hypervisor that you use is up to you but, process is still the same.
- You can use linux or windows for the base hypervisor install.


-----------------------
- Windows or Linux Installs

- Oracle VirtualBox 6.1.16 [Downloads](https://www.virtualbox.org/wiki/Downloads)

- Oracle VirtualBox Guest Extension Pack [Downloads](https://download.virtualbox.org/virtualbox/6.1.16/Oracle_VM_VirtualBox_Extension_Pack-6.1.16.vbox-extpack)

-----------------------
- Windows or Linux Installs

- VMware Workstation 16.1.0 Player Free [Downloads](https://my.vmware.com/en/web/vmware/downloads/details?downloadGroup=PLAYER-1610&productId=1039&rPId=55792)

These two are optional below.
You will need physical hardware to install.

- Vmware ESXI 6.7.OU3B [Downloads](https://my.vmware.com/en/web/vmware/downloads/details?downloadGroup=ESXI67U3B&productId=742&rPId=56014)

- Vmware ESXI 7.0 [Downloads](https://my.vmware.com/web/vmware/evalcenter?p=free-esxi7)

-----------------------
# Installation Guide ELK-SIEM Setup

- Install Guide [Document](https://github.com/watsoninfosec/ELK-SIEM/tree/main/Deployment-Guide/Installation-Guide)
- Security Configuration Guide [Document](https://github.com/watsoninfosec/ELK-SIEM/tree/main/Deployment-Guide/Security-Module)

- Wazuh Install Guide [Document](https://github.com/watsoninfosec/ELK-SIEM/tree/main/Deployment-Guide/Wazuh-Guide)
-----------------------