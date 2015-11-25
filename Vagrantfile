# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.synced_folder ".", "/vagrant"
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
  end
  config.vm.provision :shell, path: "bootstrap.sh"
  config.vm.define "master" do |node|
    node.vm.hostname = "master"
    node.vm.provision :shell, path: "bootstrap_ansible.sh"
    node.vm.network "private_network", ip: "192.168.50.100"
    node.vm.network "forwarded_port", guest: 2376, host: 2376
    node.vm.network "forwarded_port", guest: 2375, host: 2375
  end
  (1..3).each do |i|
    config.vm.define "node0#{i}" do |node|
      node.vm.hostname = "node0#{i}"
      node.vm.network "private_network", ip: "192.168.50.10#{i}"
    end
  end
  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end
end