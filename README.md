Apache Tomcat (TC) Ansible Playbook
=================================================

Note: The current scripts have only been tested on Centos/RedHat 

Install Tomcat Cluster
-----------------------------

The TC hosts file. 


Run the Ansible command
<pre>
ansible-playbook -i hosts  tomcat.yml -f 16
</pre>

This script will do the following:
* Install JDK 1.8_45 on all nodes
* Download the Apache Tomcat 8.0.23 tarball if not already present on all nodes
* Install TC on all nodes
* Configure TC
* Start all TC nodes
* Check all TC servers on all nodes are up/listening on default port


Uninstall Tomcat Cluster
-------------------------------

NOT IMPLEMENTED YET

Uninstall the Tomcat server and delete all files - <em>WARNING: THIS IS NOT UNDOABLE!</em>

Run the Ansible command
<pre>
ansible-playbook -i hosts tomcat-uninstall.yml -f 16
</pre>


