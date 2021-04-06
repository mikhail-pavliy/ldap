# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
 # config.vbguest.auto_update = false

  config.vm.provider "virtualbox" do |v|
    v.memory = 512
    v.cpus = 1
  end

  config.vm.define "ipaserver" do |server|
    server.vm.network "public_network", ip: "192.168.1.7"
    server.vm.hostname = "ipaserver"
    server.vm.provider "virtualbox" do |v|
      v.memory = 3072
      v.cpus = 2
    end
  end

  config.vm.define "test1" do |ws|
    ws.vm.network "public_network", ip: "192.168.1.8"
    ws.vm.hostname = "test1"
  end

  config.vm.define "test2" do |ws|
    ws.vm.network "public_network", ip: "192.168.1.9"
    ws.vm.hostname = "test2"
  end

  config.vm.provision "ldap", type:'ansible' do |ansible|
    ansible.inventory_path = './inventories/all.yml'
    ansible.playbook = './ldap.yml'
  end
end
