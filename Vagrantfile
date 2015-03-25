VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "fillup/centos-6.5-x86_64-minimal"
  config.vm.hostname = 'rundeck'

  config.vm.network :private_network, :ip => '192.168.1.2', :auto_network => true

  config.vm.provision "puppet" do |puppet|
    puppet.facter = {
      "node_environment" => "vagrant"
    }
    puppet.hiera_config_path = "hiera.yaml"
    puppet.working_directory = "/vagrant"
    puppet.manifest_file = "site.pp"
    puppet.module_path = ["modules"]
    puppet.options = "--environment vagrant --debug --verbose"
  end
end
