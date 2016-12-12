# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.define "rancher" do |server|
    server.vm.box = "bento/ubuntu-14.04"
    config.vm.network "private_network", type: "dhcp"
  end

  config.vm.define "node1" do |node1|
    node1.vm.box = "bento/ubuntu-14.04"
    config.vm.network "private_network", type: "dhcp"
  end

  config.vm.define "node2" do |node2|
    node2.vm.box = "bento/ubuntu-14.04"
    config.vm.network "private_network", type: "dhcp"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/rancher.yml"
		ansible.groups = {
      	"Rancher" => ["rancher"],
      	"nodes"  => ["node1", "node2"]
		}
  end  

end
