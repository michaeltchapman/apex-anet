# Decent example of vagrant-libvirt switch style setup here:
# https://github.com/skamithi/vagrant-cw-libvirt/blob/master/Vagrantfile

Vagrant.configure(2) do |config|

 config.vm.provider :libvirt do |domain|
    # increase nic adapter count to be greater than 8 for all VMs.
    domain.nic_adapter_count = 12
 end

  re_name  = "vqfx"
  pfe_name = "vqfx-pfe"

  ##############################
  ## Packet Forwarding Engine ##
  ##############################
  config.vm.define pfe_name do |vqfxpfe|
    vqfxpfe.ssh.insert_key = false
    vqfxpfe.vm.hostname = "vqfxpfe"
    vqfxpfe.vm.box = 'vqfx10k-pfe'

    vqfxpfe.ssh.username = "root"
    vqfxpfe.ssh.password = "no"

    vqfxpfe.vm.provider :libvirt do |domain|
      domain.nic_model_type = "e1000"
      domain.disk_bus = 'ide'
      domain.cpus = 2
      domain.memory = 2048
    end

    # DO NOT REMOVE / NO VMtools installed
    vqfxpfe.vm.synced_folder '.', '/vagrant', disabled: true
    vqfxpfe.vm.network "private_network", auto_config: false,
      :libvirt__tunnel_type => "udp",
      :libvirt__tunnel_port => '8501',
      :libvirt__tunnel_local_port => '9501'
  end

  config.vm.define re_name do |vqfx|
    vqfx.vm.hostname = "vqfx"
    #vqfx.vm.box = "vqfx10k-re"
    vqfx.vm.box = "junos"

    # Turn off shared folders
    vqfx.vm.synced_folder ".", "/vagrant", id: "vagrant-root", disabled: true

    vqfx.ssh.username = "root"
    vqfx.ssh.password = "Juniper"
    vqfx.ssh.shell = "cli"
    # Dont change default SSH key - already in image
    vqfx.ssh.insert_key = false

    vqfx.vm.provider :libvirt do |domain|
      domain.disk_bus = 'ide'
      domain.cpus = 2
      domain.memory = 2048
    end

    # Management ports
    vqfx.vm.network "private_network", auto_config: false,
      auto_config: false,
      :libvirt__tunnel_type => "udp",
      :libvirt__tunnel_port => '9501',
      :libvirt__tunnel_local_port => '8501'
    vqfx.vm.network "private_network", auto_config: false,
      auto_config: false,
      :libvirt__tunnel_type => "udp",
      :libvirt__tunnel_port => '9502',
      :libvirt__tunnel_local_port => '8502'
    #vqfx.vm.network 'private_network', auto_config: false, nic_type: '82540EM', virtualbox__intnet: "#{UUID}_reserved-bridge"

    # Node ports
    # Baremetal 0 - xe-0/0/0
    vqfx.vm.network "private_network",
      auto_config: false,
      :libvirt__tunnel_type => "udp",
      :libvirt__tunnel_port => '9201',
      :libvirt__tunnel_local_port => '8201'
    # Baremetal 1 - xe-0/0/1
    vqfx.vm.network "private_network",
      auto_config: false,
      :libvirt__tunnel_type => "udp",
      :libvirt__tunnel_port => '9202',
      :libvirt__tunnel_local_port => '8202'
    # Undercloud - xe-0/0/2
    vqfx.vm.network "private_network",
      auto_config: false,
      :libvirt__tunnel_type => "udp",
      :libvirt__tunnel_port => '9100',
      :libvirt__tunnel_local_port => '8100'
    # Baremetal 0 - xe-0/0/3
    vqfx.vm.network "private_network",
      auto_config: false,
      :libvirt__tunnel_type => "udp",
      :libvirt__tunnel_port => '9101',
      :libvirt__tunnel_local_port => '8101'
    # Baremetal 1 - xe-0/0/4
    vqfx.vm.network "private_network",
      auto_config: false,
      :libvirt__tunnel_type => "udp",
      :libvirt__tunnel_port => '9102',
      :libvirt__tunnel_local_port => '8102'
    # Baremetal Guest - xe-0/0/5
    vqfx.vm.network "private_network",
      auto_config: false,
      :libvirt__tunnel_type => "udp",
      :libvirt__tunnel_port => '9300',
      :libvirt__tunnel_local_port => '8300'
    vqfx.vm.network "public_network",
      auto_config: false,
      :type => 'bridge',
      :dev => 'br-admin',
      :ovs => true
  end

end
