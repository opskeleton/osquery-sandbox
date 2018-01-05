Vagrant.configure("2") do |config|

  config.vm.define :osquery do |node|
    device = ENV['VAGRANT_BRIDGE']|| 'eth0'

    pool = ENV['VAGRANT_POOL']

    config.vm.provider :libvirt do |domain, override|
       override.vm.network :public_network, :bridge => device , :dev => device
       domain.uri = 'qemu+unix:///system'
       domain.memory = 2048
       domain.cpus = 2
       domain.storage_pool_name = pool if pool
       override.vm.synced_folder './', '/vagrant', type: 'nfs', nfs_udp: false, nfs_version: 4
    end
    
    node.vm.provision :puppet do |puppet|
      puppet.manifests_path = 'manifests'
      puppet.manifest_file  = 'default.pp'
      puppet.options = "--modulepath=/vagrant/modules:/vagrant/static-modules --hiera_config /vagrant/hiera_vagrant.yaml"
    end
  end

end
