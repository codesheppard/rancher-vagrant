# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.define "rancher" do |server|
    server.vm.box = "bento/ubuntu-14.04"
    server.vm.network "private_network", ip: "192.168.111.111"
  end

  config.vm.define "node1" do |node1|
    node1.vm.box = "bento/ubuntu-14.04"
    node1.vm.network "private_network", ip: "192.168.111.222"
  end

  config.vm.define "node2" do |node2|
    node2.vm.box = "bento/ubuntu-14.04"
    node2.vm.network "private_network", ip: "192.168.111.333"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/rancher.yml"
    ansible.host_vars = {
      "rancher" => {
        "ansible_ssh_host" => "192.168.111.111",
        "ansible_ssh_port" => "22"
      },
      "node1" => {
        "ansible_ssh_host" => "192.168.111.222",
        "ansible_ssh_port" => "22"
      },
      "node2" => {
        "ansible_ssh_host" => "192.168.111.333",
        "ansible_ssh_port" => "22"
      }
    }
		ansible.groups = {
      	"Rancher" => ["rancher"],
      	"nodes"  => ["node1", "node2"]
		}
  end  

end
