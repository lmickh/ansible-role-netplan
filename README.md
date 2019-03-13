netplan
=========

Install and configure netplan.

Requirements
------------

None

Role Variables
--------------

```
netplan_file: "60_ansible.yaml"
netplan_path: "/etc/netplan"
netplan_config: {}
netplan_enabled: true
netplan_packages:
  - netplan.io
  - nplan
netplan_renderer: networkd
netplan_version: 2
netplan_wipe: false
```

Dependencies
------------

None

Example Playbook
----------------

    - hosts: some_servers
      vars:
        netplan_config:
          network:
            ethernets:
              eno1:
                addresses:
                  - 192.168.1.10/24
                gateway4: 192.168.1.1
                nameservers:
                  search: [example.com]
                  addresses: [1.1.1.1, 8.8.8.8]
              eno2:
                dhcp4: false
                dhcp6: false
                optional: true
        netplan_wipe: true
      roles:
        - {{ lmickh.netplan }}

License
-------

MIT
