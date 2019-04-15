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


  - `web_server_user` - Apache server user   
    default: `apache`
  - `web_server_group` - Apache server user's group   
    default: `apache`
  - `web_server_admin_email` - Admin's email   
    default: `root@localhost`
  - `apache_version` - Apche server version   
    default: `2.4`
  - `web_server_http_port` - Port for connection to Apache without ssl   
    default: `80`
  - `web_server_log_level` - Apache's log level (possible values are: warn,notice,info,debug,error,notice)   
    default: `warn`
  - `web_server_ssl` - Enable or disable ssl on Apache   
    default: `false`
  - `web_server_https_port` - SSl port for Apache  
    default: `443`
  - `dispatcher_root` - Dispatcher's directory   
    default: `/opt/aemDispatcherCache`
  - `dispatcher_module_version` - Version of Dispatcher module   
    default: `4.2.2`
  - `dispatcher_log_level` - Dispatcher's log level (possible values are: error, warn, error, info, debug, trace)   
    default: `warn`
  - `aem_instance_port` - Port on which Dispatcher connects to AEM instances   
    default: `4502`
  - `dispatcher_back` - List of renders for this dispatcher. For example it can take a list from inventory groups. It this case you should set it like this: `dispatcher_back: "{{ groups['aem_publishers'] }}"`
    default: `localhost`



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
- name: publisher_dispatcher_install
  hosts: publisher_dispatchers
  vars:
    dispatcher_back: "{{ groups['aem_publishers'] }}"
  roles:
    - role: ansible-role-aem-dispatcher
      dispatcher_log_level: warn

- name: authors_dispatcher_install
  hosts: author_dispatchers
  vars:
    dispatcher_back: "{{ groups['aem_authors'] }}"
  roles:
    - role: ansible-role-aem-dispatcher
      dispatcher_log_level: warn

```

License
-------
Apache

Author Information
------------------

authors:
  - Lean Delivery Team <team@lean-delivery.com>
