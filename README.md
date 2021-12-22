ansible-role-firewalld
====

Install and configure firewalld.

Requirements
------------

* RHEL8+

Role Variables
--------------

* `firewalld_packages` - list of nfs packages to install.
* `firewalld_default_zone` - default zone.
* `firewalld_add_services` - list of services to add, example:

```yaml
firewalld_add_services:
  - service: https
    zone: public # optional
```

* `firewalld_add_ports` - list of ports to add, example:

```yaml
firewalld_add_ports:
  - port: 8080
    protocol: tcp
    zone: public # optional
```

* `firewalld_add_masquerades` - list of zones to enable masquerade, example:

```yaml
firewalld_add_masquerades:
  - trusted
```

* `firewalld_add_rich_rules` - list of rich rules to add, example:

```yaml
firewalld_add_rich_rules:
  - rule: rule family="ipv4" source address="192.168.1.2" service name=mountd accept
  - rule: rule family="ipv4" source address="192.168.1.2" service name=rpc-bind accept
  - rule: rule family="ipv4" source address="192.168.1.2" service name=nfs accept
```

Dependencies
------------

Collections:

* `ansible.builtin`
* `ansible.posix`

Example Playbook
----------------

```
- hosts: my_servers
  vars:
    firewalld_add_services:
      - service: https
  roles:
    - ansible-role-firewalld
```

License
-------

GPLv3

Author Information
------------------

Vladimir Vasilev (@vladi-k)
