#  README

# To install required roles
# The installation folder is /roles because of the configuration in ansible.cfg

$ ansible-galaxy install -r requirements.yml


# To provision with vagrant run vagrant up

# To provision with digital ocean or AWS
# Uncomment in /playbooks/provision.yml file the provisioner to be used
# Play the /playbooks/provision.yml playbook on the corresponding inventory file

$ ansible-playbook -i inventories/digitalocean/inventory playbooks/deploy.yml
$ ansible-playbook -i inventories/aws/inventory playbooks/deploy.yml


## Building the VMs

  1. Download and install [VirtualBox](https://www.virtualbox.org/wiki/Downloads).
  2. Download and install [Vagrant](http://www.vagrantup.com/downloads.html).
  3. [Mac/Linux only] Install [Ansible](http://docs.ansible.com/intro_installation.html).
  4. Run `ansible-galaxy install -r requirements.yml` in this directory to get the required Ansible roles.
  5. Run `vagrant up` to build the VMs and configure the infrastructure.