aem-dispatcher role
=========
[![License](https://img.shields.io/badge/license-Apache-green.svg?style=flat)](https://raw.githubusercontent.com/lean-delivery/ansible-role-aem-dispatcher/master/LICENSE)
[![Build Status](https://travis-ci.org/lean-delivery/ansible-role-aem-dispatcher.svg?branch=master)](https://travis-ci.org/lean-delivery/ansible-role-aem-dispatcher)
[![Build Status](https://gitlab.com/lean-delivery/ansible-role-aem-dispatcher/badges/master/build.svg)](https://gitlab.com/lean-delivery/ansible-role-aem-dispatcher)
[![Galaxy](https://img.shields.io/badge/galaxy-lean__delivery.aem-dispatcher-blue.svg)](https://galaxy.ansible.com/lean_delivery/aem-dispatcher)
![Ansible](https://img.shields.io/ansible/role/d/role_id.svg)
![Ansible](https://img.shields.io/badge/dynamic/json.svg?label=min_ansible_version&url=https%3A%2F%2Fgalaxy.ansible.com%2Fapi%2Fv1%2Froles%2Frole_id%2F&query=$.min_ansible_version)

This role installs Apache httpd server and dispatcher module on RHEL and Debian based systems.

Requirements
------------

Apache httpd server version 2.2 or 2.4.

Role Variables
--------------

----------------------------------------------------------------------------------------------------------------------------------------|
| Variable         				| Required	| Default	| Choices/Values   						| Comments				   	   			|
|-------------------------------|-----------|-----------|---------------------------------------|---------------------------------------|
|webServerUser					| yes		| true		|[string]								|default value is apache				|
|webServerGroup					| yes		| true		|[string]								|default value is apache				|
|webServerAdminEmail			| yes		| true		|[string]								|default value is root@localhost		|
|apacheVersion					| yes		| true		|[string]								|default value is '2.4'					|
|webServerHTTPPort				| yes		| true		|[int]									|default value is 80					|
|webServerLogLevel				| yes		| true		|[warn,notice,info,debug,error,notice]	|default value is warn					|
|webServerSSL					| yes		| true		|true\false								|default value is false					|
|webServerHTTPsPort				| no		| true		|[int]									|default value is 443					|
| dispatcher_root         		| yes		| true		|[string] 	  							|default value is /opt/aemDispatcherCache|
| dispatcher_module_version  	| yes		| true		|[string]								|default value is '4.2.2'				|
| dispatcherLogLevel      		| yes		| true		|error/warn/error/info/debug/trace		|default value is warn		 			|
| aem_instance_port				| yes		| false		|[int]									|port for connection to aem instance	|
| render                		| no		| false		|[comma-sep list]   					|list of renders for this dispatcher	|



Dependencies
------------

We recomend to use this role in the scope with next roles:
    - lean-delivery/ansible-role-aem-node
    - lean-delivery/ansible-role-aem-pipeline

But you can also use only this one role if you already have some infrastracture in Adobe Experience Manager.


Example Playbook
----------------

```yaml
---
- hosts: all
  roles:
    - role: ansible-role-aem-dispatcher
  vars:
    aemInstancePort: 4502
    render: localhost
```

License
-------
Apache

Author Information
------------------

authors:
  - Lean Delivery Team <team@lean-delivery.com>
