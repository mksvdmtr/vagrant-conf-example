# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/8"
  config.vm.network "public_network", bridge: "enp0s31f6"
  config.vm.define "c8-1"
  config.vm.define "c8-2"

  config.vm.provider "virtualbox" do |vb|
     vb.gui = false
     vb.memory = "1024"
     vb.cpus = 1
  end



  config.vm.provision "shell" do |s|
    s.inline = <<-SHELL
    sed -i s/SELINUX=enforcing/SELINUX=disabled/ /etc/selinux/config
    reboot
    SHELL
  end

end

