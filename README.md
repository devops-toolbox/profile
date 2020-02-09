Role Name
=========

profile: Profile

[![Build Status](https://travis-ci.org/cmihai-ansible/profile.svg?branch=master)](https://travis-ci.org/cmihai-ansible/profile)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.profile](https://galaxy.ansible.com/devops-toolbox.profile)

```bash
ansible-galaxy install devops-toolbox.profile
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
profile_packages_state: present
profile_remove_packages: true
profile_enable_service: true
profile_enable_selinux: true
profile_copy_templates: true
profile_firewall_configure: true
profile_firewall_rules:
  - service: ssh
  - port: 3389
profile_users:
  - user: devops
    group: docker
profile_selinux_booleans:
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
- name: Install profile on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: profile is configured
      import_role:
        name: devops-toolbox.profile
      vars:
        profile_packages_state: present
        profile_remove_packages: true
        profile_enable_service: true
        profile_enable_selinux: true
        profile_copy_templates: true
        profile_firewall_configure: true
        profile_firewall_rules:
          - service: ssh
          - port: 3389
        profile_users:
          - user: devops
            group: docker
        profile_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: profile
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
