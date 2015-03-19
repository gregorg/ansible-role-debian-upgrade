Debian Upgrade
==============

Upgrade a Debian OS.

Only upgrade from Squeeze to Wheezy is supported and tested.

Visit [Ansible Galaxy](https://galaxy.ansible.com/list#/roles/3177) for usage.


Role Variables
--------------

* `upgrade_from_debian`: Debian release name from which to upgrade. Only used for checking.
    * Default: `squeeze`
* `upgrade_to_debian`: Debian relase name to upgrade to.
    * Default: `wheezy`
* `pkgs_to_install_after_upgrade`:
    * Default: empty


Example Playbook
----------------


```yaml
- name: DEBIAN DIST UPGRADE
  hosts: all
  gather_facts: yes
  serial: 1
  roles:
   - { role: debian-upgrade,
       pkgs_to_install_after_upgrade: [
       firmware-bnx2,
       ]
     }
```


License
-------

MIT

