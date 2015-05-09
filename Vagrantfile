# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
  end

  config.vm.network "forwarded_port", guest: 80, host: 3334

  config.vm.synced_folder "./", "/var/www"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisionings/site.yml"
    ansible.limit = "default"
    ansible.groups = {
      "vagrant" => ["default"],
    }
  end
end
