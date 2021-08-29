Role Name
=========

Group of task for configuring a kubernetes worker node.

Requirements
------------

Requires `common` role

Role Variables
--------------

Dependencies
------------

Requires `common` role.

Example Playbook
----------------

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
