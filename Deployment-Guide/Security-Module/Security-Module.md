# Securing Our ELK-SIEM

This guide will walk you through on setting up security of your ELK-SIEM so that basic security features will be enabled.

- First Step navigate to the Elasticsearch folder location.

~~~
cd  /usr/share/elasticsearch/
~~~

- List the contents of the directory:

~~~
ls
~~~

- Now execute elasticsearch-certutil and create a --pem file:

~~~
sudo bin/elasticsearch-certutil ca --pem
~~~

This will prompt you to create the Certificate zip file. You can leave it to the defaults. We will rename the cert later!

Next: Install unzip application.

- Install unzip:

~~~
sudo apt install zip unzip -y
~~~

- Then unzip the elastic-stack-ca.zip file:

~~~
sudo unzip elastic-stack-ca.zip
~~~

- The cert folder name should be **ca**
- Then move the ca into the root folder: 

~~~
sudo mv ca /
~~~

- Then cd into the root directory:

~~~
cd /
~~~

At this point once the cert has been unzipped you can change the name by copying the file into another file.

- Example:

~~~
cd ca/
sudo cp ca.crt mycertname.crt
sudo cp ca.key mycertname.key
~~~

This is just to change the name from default if you want to.

Note: You must change the values to match the location path of the certs.


Now lets edit the Kibana.yml & elasticsearch.yml files and add this security feature at the end of the file::

- Security Feature:

~~~
xpack.security.enabled: true
~~~

- Edit these files:

~~~
sudo nano /etc/kibana/kibana.yml
sudo nano /etc/elasticsearch/elasticsearch.yml
~~~

- Now lets restart Kibana:

~~~
sudo systemctl restart kibana
~~~


- Lets go back and edit this file again:
~~~
sudo nano /etc/kibana/kibana.yml
~~~

- Now uncomment (#) hash signs and edit the values below to match your values you created.


~~~
server.ssl.enabled: true
server.ssl.certificate: /ca/ca.crt
server.ssl.key: /ca/ca.key
~~~

- Now restart Kibana:

~~~
sudo systemctl restart kibana
~~~

Once that is done we must create the system default users to be able to login and create our own username for access.

- Run these command to create system users:

~~~
cd /usr/share/elasticsearch/bin
sudo ./elasticsearch-setup-passwords auto
~~~

- Now we must go back again and add our elastic user login creds:

~~~
sudo nano /etc/kibana/kibana.yml
~~~

- Now look for this field and add your password for this account:

~~~
elasticsearch.username: "kibana_system"
elasticsearch.password: "oZdTyaMMxCLaNmaW9udf"
~~~

This will create the system users for the login.

Note: Copy the user names and document them for safe keeping, because you will need these names later in your setup.

Once this process is setup you will now a secure setup of Elasticseach + Kiban ELK-SIEM.

## Now you can login and explore!

# Conclusion

We now have our security features enabled and working, so at this point you can navigate to the: **Wazuh Setup Guide** 
https://github.com/watsoninfosec/ELK-SIEM/blob/main/Deployment-Guide/Wazuh-Guide/Setup-Guide.md

