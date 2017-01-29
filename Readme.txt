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