Ansible Role: Tomcat Deploy
===========================

This role deploy a list of Tomcat wars and create a nginx vhost for every war, optionally.

Requirements
------------

This Ansible playbook is meant to be run on a FRESH never used server, virtual machine or container.

Requires a tomcat installation ( Optional: squintans.tomcat9 role )

Requires a nginx installation if vhost nginx is desirable ( Optional: squintans.nginx role )

Role Variables
--------------

**defaults/main.yml:***
```
# Wars to deploy. War file must be on files.
wars:
  - name: hello01
    war: hello01.war
  - name: hello02
    war: hello02.war

# Tomcat install path
tomcat_deploy_tomcat_install: '/opt/tomcat'

# Set to True to create nginx vhost proxy to war app. ( Requires squintans.nginx role )
tomcat_nginx_vhost: False
```

Role Templates
==============

```
nginx_war.conf.j2
```

Role Files
==========

```
hello01.war
hello02.war
```

Dependencies
------------

None.

Example Playbook
----------------

**Example with prompt:**
```
- hosts: "{{ vm }}"
  gather_facts: True

  vars_prompt:
    - name: "vm"
      prompt: "VM"
      private: no

  roles:
    - { role: squintans.tomcat_deploy }
```

Playbook Call
=============
```
ansible-playbook -i inventory.yml play.yml
```

License
-------

BSD

Author Information
------------------
This role was created in 2019 by Serafín Quintáns - [@squintans](http://www.linkedin.com/in/serafin-quintans/)

