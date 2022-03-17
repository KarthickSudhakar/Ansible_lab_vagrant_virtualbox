# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  
  config.vm.provider "virtualbox" do |rs|
    rs.memory = 2048
    rs.cpus = 2
  end

  # Will not check for box updates during every startup.
  config.vm.box_check_update = false


  # Master node where ansible will be installed
  config.vm.define "controller" do |controller|
    controller.vm.box = "ubuntu/focal64"
    controller.vm.hostname = "controller.anslab.com"
    controller.vm.network "private_network", ip: "192.168.10.3"
    controller.vm.provision "shell", path: "bootstrap.sh"
    controller.vm.provision "file", source: "key_gen.sh", destination: "/home/vagrant/"
  end

  # Managed node 1.
  config.vm.define "m1" do |m1|
    m1.vm.box = "ubuntu/focal64"
    m1.vm.hostname = "managed1.anslab.com"
    m1.vm.network "private_network", ip: "192.168.10.4"
    m1.vm.provision "shell", path: "bootstrap.sh"
  end

  # Managed node 2.
  config.vm.define "m2" do |m2|
    m2.vm.box = "ubuntu/focal64"
    m2.vm.hostname = "managed2.anslab.com"
    m2.vm.network "private_network", ip: "192.168.10.5"
    m2.vm.provision "shell", path: "bootstrap.sh"
  end

end
