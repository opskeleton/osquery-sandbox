Vagrant.configure("2") do |config|

  config.vm.define :osquery do |node|
    node.vm.box = 'ubuntu-16.04.3_puppet-4.10.8'
    node.vm.hostname = 'osquery.local'

    node.vm.provision :puppet do |puppet|
      puppet.manifests_path = 'manifests'
      puppet.manifest_file  = 'default.pp'
      puppet.options = "--modulepath=/vagrant/modules:/vagrant/static-modules --hiera_config /vagrant/hiera_vagrant.yaml"
    end
  end

end
