VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "centos-63-x64"
  config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/centos-63-x64.box"
  config.vm.hostname = 'rundeck'

  config.vm.network :private_network, :ip => '192.168.1.2', :auto_network => true

  config.vm.provision "puppet" do |puppet|
    puppet.facter = {
      "node_environment" => "vagrant"
    }
    puppet.hiera_config_path = "hiera.yaml"
    puppet.working_directory = "/vagrant"
    puppet.manifest_file = "site.pp"
    puppet.module_path = ["modules","site/modules"]
    puppet.options = "--environment vagrant --debug --verbose"
  end
end
