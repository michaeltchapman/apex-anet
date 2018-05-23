This role uses customises an apex install to use ansible-networking in place
of networking-generic-switch, and uses a vendor switch emulator for virtual
baremetal networking

Sample playbook:
```
- hosts: localhost
  connection: local
  gather_facts: no
  vars:
    working_dir: "/place-with-much-disk-space"

  # build images, boot virtual switches and deploy apex
  roles:
    - apex-anet/virthost/setup

  # register the overcloud via the undercloud
- hosts: undercloud 
  roles:
    - apex-anet/undercloud/setup

  # configure overcloud controllers for networking-ansible
- hosts: overcloud_controllers 
  roles:
    - apex-anet/overcloud/setup

  # provision network and configure flavors
- hosts: undercloud
  roles:
    - apex-anet/undercloud/network_flavor
 
  # create new baremetal node
- hosts: localhost 
  connection: local
  roles:
    - apex-anet/virthost/add_ironic_node
 
  # add new baremetal node to overcloud ironic
- hosts: undercloud 
  roles:
    - apex-anet/undercloud/add_ironic_node
 
  # deploy to new baremetal node
- hosts: undercloud 
  roles:
    - apex-anet/undercloud/deploy_ironic_node
```
