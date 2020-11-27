# ELK-SIEM Deployment Guide

- Creating an Elasticsearch + Kibana SIEM. 

# Install Guide & Build Instructions

This setup guide will show you how to create an Elasticsearch + Kibana ELK-SIEM.

I have listed some install steps below to help you re-create the same install build that I created. This will be a simple install out-of-box deployment.

## Requirements

- **Ubuntu** 18.04 or 20.04 LTS Linux distribution.
- **Java** 8 openjdk-8-jdk.
- **Git repository** ppa:git-core/ppa
- **Elastic repository** 
- **kibana repository**
- **Putty or SSH Terminal**

- **Some of these Requiements are already installed in Ubuntu!**

## Ubuntu 18.04 & 20.04 LTS

 First we need to install ubuntu, this can be on a VMware or Oracle VirtualBox setup. Or if you have the physical hardware to spare that will work as well.

Note: Just make sure you have SSH access enabled once the server install is completed and know the IP address of the machine. Or that you can login through the GUI and open a Terminal.

## Installation of utilities

The ELK stack requires Java 8 to be installed. Some components are compatible with Java 9, but not Logstash

- Before we install our ELK-SIEM, we will need to update our Ubuntu Distro first.
- Open a Terminal or SSH connection and login and type this commands.

~~~
sudo apt-get update && apt-get upgrade -y
~~~ 

- Once that is done perform a Distro upgrade to finish last few upgrades.

~~~
sudo apt-get dist-upgrade -y
~~~

- Now lets reboot the system and finish our deployment.

Note: Lets check your Java version to see if it is installed, enter the following:

~~~
java -version
~~~

* If Java is installed and it's the right version, skip this step!

- Install java Version 8:

~~~
sudo apt-get install openjdk-8-jdk -y
java -version
~~~

Now lets add our Elastcisearch Repos into our system:

- Elastic repositories enable access to all the open-source software in the ELK stack. To add them, start by importing the GPG key.

+ Add Elastic Repository
~~~

wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
~~~

- The system should respond with OK.

Next, install the apt-transport-https package:

~~~
sudo apt-get install apt-transport-https -y
~~~

Now add the Elastic repository to your system’s repository list:
~~~
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list
~~~

Prior to installing Elasticsearch, update the repositories by entering:

~~~
sudo apt-get update -y
~~~

Install Elasticsearch with the following command:

~~~
sudo apt-get update && sudo apt-get install elasticsearch -y
~~~

Do a systemctl daemon reload.
~~~
sudo systemctl daemon-reload
~~~

## Configure Elasticsearch

Elasticsearch uses a configuration file called **.yml** to control how it behaves. Open the configuration file for in a text editor of your choice.Either nano or vi.
 **We will be using nano**:

~~~
sudo nano /etc/elasticsearch/elasticsearch.yml
~~~

- You should see a configuration file with several different entries and descriptions. Scroll down to find the following entries:

~~~
network.host: localhost
http.port: 9200
~~~

- Uncomment the lines by deleting the hash (#) sign at the beginning of both lines and replace **localhost** with you ip address.

- Just below, find the Discovery section. We are adding one more line, as we are configuring a single node cluster:

~~~
discovery.type: single-node
~~~

- Start the Elasticsearch service by running a systemctl command:


~~~
sudo systemctl start elasticsearch.service
~~~

- No verify that the service is running:
~~~
sudo service elasticsearch status
~~~

This may take some time for the serivce to run, but once it does we will need to check that it is installed.

- Type this command in:
~~~
http://my_ip_address_here://9200
~~~

Once you hit enter you shoud see something like this:

~~~
{
  "name" : "elk-siem",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "LDr0LpmnbQyuk09lqgeVof",
  "version" : {
    "number" : "7.10.0",
    "build_flavor" : "default",
    "build_type" : "deb",
    "build_hash" : "90s9d6f23348d0374a0f3f5c6e8f3a7997850f89",
    "build_date" : "2020-11-09T21:30:33.964949Z",
    "build_snapshot" : false,
    "lucene_version" : "8.7.0",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}
~~~

This means that the system in running Elasticsearch and it has been installed. Now lets enable it run on boot.

- Enable Elasticsearch to start on boot:

~~~
sudo systemctl enable elasticsearch.service
~~~

- You can also test Elasticsearch by running this command:

~~~
curl –X GET “my_ip_address_here:9200”
~~~

- Now that we have Elasticsearch install and running, lets install Kibana.

## Configure Kibana 

Kibana is a graphical user interface for parsing and interpreting collected log files.

- lets run the following command to install Kibana:

~~~
sudo apt-get install kibana -y
~~~

- Now lets configure Kibana.

~~~
sudo nano /etc/kibana/kibana.yml
~~~






## Output Samples in PDF format

### Article style

![Article](img/article.pdf.png)

### Document style

![Document](img/document.pdf.png)

### Keynotes style

![Keynotes](img/keynotes.pdf.png)

