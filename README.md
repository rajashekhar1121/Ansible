Apache Tomcat (TC) Ansible Playbook
=================================================

Note: The current scripts have only been tested on Centos/RedHat 

Install Tomcat Cluster
-----------------------------

The TC hosts file. 

This file contains 6 groups of servers:
[(ch|as|po)-tomcat] - Chicago|Potomac|Ashburn DC specific nodes


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

NOTES:
-------

In some environments the Apache commons-codec causes a classpath conflict due to a library conflict with the Enterprise Geocoder g1ClientSDK.  It uses an oudated commons-codec and when the Base64 class from it is loaded first, the attemptive REST call fails with NoSuchMethod error.  To fix download at least the commons-codec-1.5.jar and append to bootclasspath by editing the catalina.sh script on the affected system:
<pre>
-Xbootclasspath/a:<jar_dir>/commons-codec-1.5.jar \
</pre>

This will allow the server to start normally.  The old g1ClientSDK will work with a newer codec library.  
