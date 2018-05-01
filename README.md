This role uses customises an apex install to use ansible-networking in place
of networking-generic-switch, and uses a vendor switch emulator for virtual
baremetal networking

Sample playbook:
```
- hosts: localhost
  connection: local
  gather_facts: no

  vars:
    working_dir: "/home/michapma/anet-testing-repo"

  roles:
    - apex-anet
```

