# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.network "public_network", ip: "192.168.40.170", bridge: "Hyper-V Virtual Ethernet Adapter #2"
  config.vm.synced_folder "./ansible", "/ansible"
  config.vm.provider "virtualbox" do |vb|
  # Display the VirtualBox GUI when booting the machine
      vb.gui = true
  # Customize the amount of memory on the VM:
      vb.memory = "1024"
      vb.name = "vm-servidor-nginx"
      vb.cpus = 2
  end
  config.vm.provision "shell", inline: <<-SHELL
       #apt update
       sudo useradd -m arimateia.junior -s /bin/bash
       apt install ansible -y
       ansible-playbook --connection=local /ansible/playbook.yml
  SHELL
end
