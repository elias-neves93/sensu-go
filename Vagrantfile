# -*- mode: ruby -*-
# vi: set ft=ruby :

machines = {
	"backend-1" => {"memory"=>"2048", "cpus"=>"2", "ip" => "100" },
	"backend-2" => {"memory"=>"2048", "cpus"=>"2", "ip" => "101" },
	"backend-3" => {"memory"=>"2048", "cpus"=>"2", "ip" => "102" },
	"agent-1" => {"memory"=>"1024", "cpus"=>"1", "ip" => "110" },
	"agent-2" => {"memory"=>"1024", "cpus"=>"1", "ip" => "111" },
	"agent-3" => {"memory"=>"1024", "cpus"=>"1", "ip" => "112" },
}

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  machines.each do |name,conf|
    config.vm.define "#{name}" do |machine|
      machine.vm.network "private_network", ip: "192.168.88.#{conf["ip"]}"
      machine.vm.hostname = "#{name}.lab.local"
      machine.vm.provider "virtualbox" do |vb|
        vb.cpus = "#{conf["cpus"]}"
				vb.memory = "#{conf["memory"]}"
	vb.name = "#{name}"
	vb.gui = false
      end
    end
  end
	config.vm.provision "shell", inline: <<-SHELL
	 sudo apt update && sudo apt install python -y
 SHELL
end
