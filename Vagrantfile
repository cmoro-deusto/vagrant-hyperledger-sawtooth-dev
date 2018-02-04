# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.define "sawtoothdev" do |sawtoothdev|
    sawtoothdev.vm.hostname = "sawtoothdev"
    sawtoothdev.vm.provider :virtualbox do |vb|
      vb.name = "sawtoothdev"
    end

  sawtoothdev.vm.provision 'preemptively give others write access to /etc/ansible/roles', type: :shell, inline: <<~'EOM'
    sudo mkdir /etc/ansible/roles -p
    sudo chmod o+w /etc/ansible/roles
  EOM

  sawtoothdev.vm.provision 'ansible', run: 'always', type: :ansible_local do |ansible|
    ansible.galaxy_role_file = '/vagrant/requirements.yml'
    ansible.galaxy_roles_path = '/etc/ansible/roles'
    ansible.galaxy_command = 'ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path}'
    ansible.playbook = '/vagrant/playbook.yml'
  end

  sawtoothdev.vm.network "public_network"
  sawtoothdev.vm.network "forwarded_port", guest: 8008, host: 8008, protocol: "tcp", host_ip: "127.0.0.1"
  sawtoothdev.vm.network "forwarded_port", guest: 4200, host: 4200, protocol: "tcp", host_ip: "127.0.0.1"

  # config.vm.box_check_update = false

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
  end
  end
end
