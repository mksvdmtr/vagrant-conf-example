# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/buster64"
  config.vm.network "public_network"
  config.vm.hostname = "deb10-1"
  config.vm.define "deb10-1"

  config.vm.provider "virtualbox" do |vb|
     vb.gui = true
     vb.name = "deb10-1"
     vb.memory = "1024"
     vb.cpus = 1
  end

  config.vm.provision "shell" do |s|
    ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
    s.inline = <<-SHELL
    mkdir /root/.ssh
      echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
      echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
    # Add more commands, for example: 
    # apt install mc gcc vim ...
    echo "#####################"
    echo "IP: $(ip -4 a | grep inet | awk '{print $2}' | tail -1)"
    echo "#####################"
    SHELL
  end

end

