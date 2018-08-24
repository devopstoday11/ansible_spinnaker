# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"

  # Spinnaker
  (1..1).each do |i|
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 10000
      vb.cpus = 4
    end

    config.vm.define "spinnaker0#{i}" do |server|
      server.vm.hostname = "spinnaker0#{i}"
      server.vm.network "private_network", ip: "10.0.4.4#{i}"
    end
  end

  # Provision
  config.vm.provision "shell", path: "provision.sh"
  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/authorized_keys"

end
