# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.provider "virtualbox" do |vb|
     vb.memory = "512"
  end

  config.vm.provision "ansible" do |ansible|
      ansible.playbook = "music.yaml"
      ansible.become = true
      ansible.verbose = true
  end

end
