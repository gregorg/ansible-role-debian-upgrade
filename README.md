Debian Upgrade
==============

Upgrade a Debian OS.

Only upgrade from Squeeze to Wheezy is supported and tested.

Visit [Ansible Galaxy](https://galaxy.ansible.com/list#/roles/3177) for usage.


Warnings
--------

By default, the server is reboot after a successfull dist-upgrade, but you can disable this behavior.

I highly recommend to limit playbook execution to one server :

```
ansible-playbook -l ~myserver playbook.yml
```


Role Variables
--------------

* `upgrade_from_debian`: Debian release name from which to upgrade. Only used for checking.
    * Default: `squeeze`
* `upgrade_to_debian`: Debian relase name to upgrade to.
    * Default: `wheezy`
* `pkgs_to_install_after_upgrade`:
    * Default: empty


Role Tags
---------

You can use tags to skip some hard tasks :
* `reboot`: the most important, you can skip reboot at the end of a successfull upgrade
* `checks`: if for some reason this role failed in middle upgrade, you can skip this tags to disable release checking
* `purge`: to skip packages purge (old kernels and `apt-get autoremove`
* `custom`: to skip installation of custom debian packages

```
ansible-playbook playbook.yml --skip-tags checks,reboot
```

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

