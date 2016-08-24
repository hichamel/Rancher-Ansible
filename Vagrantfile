# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  config.vm.define :rancher do |rancher|
      rancher.vm.box = "hashicorp@precise64"
      rancher.vm.box_url = "http://files.vagrantup.com/precise64.box"
      rancher.vm.hostname = "rancher"
      rancher.vm.network :private_network, ip: "10.0.15.10"
      rancher.vm.provider "virtualbox" do |vb|
        vb.memory = "256"
      end
      
end

    # create load balancer
  config.vm.define :lb do |lb|
      lb.vm.box = "hashicorp@precise64"
      lb.vm.box_url = "http://files.vagrantup.com/precise64.box"
      lb.vm.hostname = "lb"
      lb.vm.network :private_network, ip: "10.0.15.11"
      lb.vm.network "forwarded_port", guest: 80, host: 8080
      lb.vm.provider "virtualbox" do |vb|
        vb.memory = "256"
      end
  end

     # create mySQL server
  config.vm.define :mysql do |mysql|
      mysql.vm.box = "hashicorp@precise64"
      mysql.vm.box_url = "http://files.vagrantup.com/precise64.box"
      mysql.vm.hostname = "mysql"
      mysql.vm.network :private_network, ip: "10.0.15.12"
      mysql.vm.provider "virtualbox" do |vb|
        vb.memory = "256"
      end
  end

    # create some web servers
  (1..2).each do |i|
    config.vm.define "wp#{i}" do |wp|
        wp.vm.box = "hashicorp@precise64"
        wp.vm.box_url = "http://files.vagrantup.com/precise64.box"
        wp.vm.hostname = "wp#{i}"
        wp.vm.network :private_network, ip: "10.0.15.2#{i}"
        #wp.vm.network "forwarded_port", guest: 80, host: "808#{i}"
        wp.vm.provider "virtualbox" do |vb|
          vb.memory = "256"
        end
    end
  end
  

end 
