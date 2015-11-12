# -*- mode: ruby -*-

# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  #box
  config.vm.box = "ubuntu/trusty64"

  #ssh
  config.ssh.forward_agent = true

  #networking
  #config.vm.network :private_network, ip: "192.168.111.222"

  #shared folders
  config.vm.synced_folder ".", "/home/vagrant/application"
  config.vm.synced_folder "shared/", "/home/vagrant/shared"

  #memory up
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", "1024"]
  end

  #provisions the environment
  config.vm.provision "ansible" do |ansible|
    #ansible.verbose = "vvv"
    ansible.playbook = "provisioning/mean.yml"
  end

  #ports
  config.vm.network "forwarded_port", guest: 27017, host: 27017
  # config.vm.network "forwarded_port", guest: 3306, host: 3307
end