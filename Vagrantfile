# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.network "forwarded_port", guest: 80, host: 8080

  # quick fix for permissions
  config.vm.synced_folder "./", "/vagrant", :id => "vagrant-root", :mount_options => ["dmode=777", "fmode=766"]
  
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "512"]
  end
  
  config.vm.provision :shell do |shell|
    shell.inline = "apt-get update"
    shell.inline = "gem install chef --version 11.6.0 --no-ri --no-rdoc --conservative"
  end

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["vm/cookbooks", "vm/site-cookbooks"]
    chef.roles_path = "vm/roles"
    chef.add_role "default"
  end
end
