# -*- mode: ruby -*-
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.hostname = "postgresql"
  config.vm.box = "chef/ubuntu-14.10"

  config.vm.network "forwarded_port", guest: 5432, host: 5432

  config.vbguest.auto_update=false
  
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook   = "playbook.yml"
    ansible.verbose    = "vvv"
    ansible.limit      = "all"
    ansible.extra_vars = { postgresql_verion: '9.4' }
  end
end
