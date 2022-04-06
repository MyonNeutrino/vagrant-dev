# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "archlinux/archlinux"

  config.vm.synced_folder "~/Dokumente/vagrant", "/home/chrifl/Dokumente/host", owner: "chrifl", group: "chrifl"
  config.vm.synced_folder "~/.ssh", "/home/chrifl/.ssh", owner: "chrifl", group: "chrifl"

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "6144" # 4096 + 2048 = 6144
    #vb.customize ["modifyvm", :id, "--monitorcount", "2"]
    vb.customize ["modifyvm", :id, "--vram", "256"]
    vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
    vb.gui = true
  end

  # PHP Dev Environment
  config.vm.define "php-dev" do |php|
    php.vm.hostname = "php.dev"

    php.vm.network :private_network, ip: "192.168.60.4"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.verbose = true
  end

end
