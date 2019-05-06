Role Name
=========

Syslog-NG Upgrade role with two way encrypted communication using certificates for OULib.

Requirements
------------

* A target system running CentOS7x.
* [OULibraries.syslogng](https://github.com/OULibraries/ansible-role-syslogng)
* Make Tools
  * libtool 
  * make 
  * autoconf 
  * automake 

Role Variables
--------------

Server and Client Vars are defined in OULibraries.syslogng

Source Tarball location and version is defined in Defaults and can be adjusted in vars if version drifts or needs are not met. 
 

Dependencies
------------

* [OU Libraries Centos7 Role](https://github.com/OULibraries/ansible-role-centos7)
* [OU Libraries Users Role](https://github.com/OULibraries/ansible-role-users)

This role configures the sever for syslog destination. The companion role is the Syslog-NG Client Role, which is used to configure each client on the network. Once the server has been deployed on the network, and you have deployed your client(s) using the companion ansible-role-syslog-client playbook, simply copy the client SSL certificate into your my-vars.yml file and insert the client IP address and domain name.

* [OU Libraries Syslog-NG Client Role](https://github.com/OULibraries/ansible-role-syslogng-client)


Example Playbook
----------------

Initial deployment of the server role can be run without the necessary client information skipping the "client" tag. 

	ansible-playbook <playbook name> --skip-tags "client"

After the server and client(s) have both been deployed, rerunning of the server playbook with the "client" tag will insert the necessary information in the server config to allow two way encrypted communication

	ansible-playbook <playbook name> --tags "client"

Make sure to change the client variables in the my-vars.yml file for each client on the network. 

License
-------

[MIT](https://github.com/OULibraries/ansible-role-syslogng/blob/master/LICENSE)

Author Information
------------------

Cody Bennett @ OU Libraries
