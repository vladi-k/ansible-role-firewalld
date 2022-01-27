ansible-role-firewalld
====

Install and configure firewalld. By default this role will open immediately and permanently the rules from the variables below.

Requirements
------------

* RHEL8+

Role Variables
--------------

* `firewalld_packages` - list of nfs packages to install.
* `firewalld_default_zone` - default zone.
* `firewalld_services` - list of services to manage, example:

```yaml
firewalld_services:
  - service: https
    zone: public # optional
  - service: ssh
    zone: public
    state: disabled
```

* `firewalld_ports` - list of ports to manage, example:

```yaml
firewalld_ports:
  - port: 8080
    protocol: tcp
    zone: public # optional
```

* `firewalld_add_masquerades` - list of zones to enable masquerade, example:

```yaml
firewalld_add_masquerades:
  - trusted
```

* `firewalld_rich_rules` - list of rich rules to manage, example:

```yaml
firewalld_rich_rules:
  - rule: rule family="ipv4" source address="192.168.1.2" service name=mountd accept
  - rule: rule family="ipv4" source address="192.168.1.2" service name=rpc-bind accept
  - rule: rule family="ipv4" source address="192.168.1.2" service name=nfs accept
```

* `firewalld_sources` - list of sources, example:

```yaml
firewalld_sources:
  - source: 192.168.1.2
    zone: trusted
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
    firewalld_services:
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
