Role Name
=========

ca: Ca

[![Build Status](https://travis-ci.org/cmihai-ansible/ca.svg?branch=master)](https://travis-ci.org/cmihai-ansible/ca)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.ca](https://galaxy.ansible.com/devopstoolbox.ca)

```bash
ansible-galaxy install devopstoolbox.ca
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
ca_packages_state: present
ca_remove_packages: true
ca_enable_service: true
ca_enable_selinux: true
ca_copy_templates: true
ca_firewall_configure: true
ca_firewall_rules:
  - service: ssh
  - port: 3389
ca_users:
  - user: devops
    group: docker
ca_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install ca on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: ca is configured
      import_role:
        name: devopstoolbox.ca
      vars:
        ca_packages_state: present
        ca_remove_packages: true
        ca_enable_service: true
        ca_enable_selinux: true
        ca_copy_templates: true
        ca_firewall_configure: true
        ca_firewall_rules:
          - service: ssh
          - port: 3389
        ca_users:
          - user: devops
            group: docker
        ca_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: ca
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
