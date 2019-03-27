# coding: utf-8

Vagrant.require_version ">= 1.6.0"

CONSUL_BINARY = "consul-enterprise_1.0.7+ent_linux_amd64.zip"
VAULT_BINARY = "vault-enterprise_0.10.1+ent_linux_amd64.zip"

Vagrant.configure("2") do |config|

  %w(consul0 consul1 consul2 consul3 consul4).each_with_index do |nodename, consul_index|

    config.vm.define "#{nodename}", autostart: true do |thisnode|
      thisnode.vm.box = "ubuntu/xenial64"
      thisnode.vm.box_version = "20190325.0.0"

      thisnode.vm.provider "virtualbox" do |vb|
        vb.linked_clone = true
        vb.memory = "512"
      end

      ip_address = "10.13.37.#{20 + consul_index}"

      thisnode.vm.hostname = "#{nodename}"

      thisnode.vm.network "private_network", ip: ip_address

      thisnode.vm.provision "hosts", autoconfigure: true, sync_hosts: true
      thisnode.vm.provision "shell", path: "consul/consul-server.sh"
    end
  end

  %w(consulnew0 consulnew1 consulnew2 consulnew3 consulnew4).each_with_index do |nodename, consul_index|

    config.vm.define "#{nodename}", autostart: true do |thisnode|
      thisnode.vm.box = "ubuntu/xenial64"
      thisnode.vm.box_version = "20190325.0.0"

      thisnode.vm.provider "virtualbox" do |vb|
        vb.linked_clone = true
        vb.memory = "512"
      end

      ip_address = "10.13.37.#{30 + consul_index}"

      thisnode.vm.hostname = "#{nodename}"

      thisnode.vm.network "private_network", ip: ip_address

      thisnode.vm.provision "hosts", autoconfigure: true, sync_hosts: true
      thisnode.vm.provision "shell", path: "consul/consul-server-new.sh"
    end
  end

end
