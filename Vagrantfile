# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Base VM OS configuration.
  config.vm.box = "geerlingguy/ubuntu1404"
  config.vm.synced_folder '.', '/vagrant', disabled: true
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.memory = 512
    v.cpus = 1
  end

  # Define required VMs with name and static private IP addresses.
  boxes = [
    { :name => "nginx", :ip => "192.168.2.40" },
#    { :name => "railsapp", :ip => "192.168.2.50" },
#    { :name => "mysql", :ip => "192.168.2.60" }
  ]

  # Provision each of the VMs.
  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.hostname = opts[:name]
      config.vm.network :private_network, ip: opts[:ip]

      # Provision all the VMs using Ansible after last VM is up.
      if opts[:name] == "nginx"
#      if opts[:name] == "mysql"
        config.vm.provision "ansible" do |ansible|
          ansible.playbook = "playbooks/configure.yml"
          ansible.inventory_path = "inventories/vagrant/inventory"
          ansible.limit = "all"
          ansible.extra_vars = {
            ansible_ssh_user: 'vagrant',
            ansible_ssh_private_key_file: "~/.vagrant.d/insecure_private_key"
          }
          end
      end
    end
  end

end
