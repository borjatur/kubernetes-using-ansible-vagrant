Role Name
=========

Group of task for configuring a kubernetes master node.

Requirements
------------

Role Variables
--------------

Dependencies
------------

Requires `common` role

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: all
  become: true
  roles:
    - role: './roles/common'
    - role: './roles/master-node'
```

License
-------

MIT

Author Information
------------------
borja.tur@gmail.com


