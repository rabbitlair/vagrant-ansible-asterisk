# vi: set ft=ruby :

# Include config from settings.yml
require 'yaml'
vconfig = YAML::load_file("settings.yml")

# Configuration
boxipaddress = vconfig['boxipaddress']
boxname = vconfig['boxname']
interface = vconfig['interface']
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Configure virtual machine options.
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"
  config.vm.box = "trusty64"
  config.vm.hostname = boxname
  config.vm.network :public_network, ip: boxipaddress, bridge: interface

  # Configure virtual machine setup.
  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--memory", 512]
  end

  # SSH Set up.
  config.ssh.forward_agent = true

  # Set machine name.
  config.vm.define boxname do |t|
  end

  # Provision vagrant box with ansible.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision/deploy.yml"
    ansible.host_key_checking = false
    ansible.extra_vars = {user:"vagrant"}
  end

end

