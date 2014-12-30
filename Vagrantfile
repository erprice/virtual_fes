# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.network :private_network, ip: "192.168.33.10"
  # Hadoop web UI ports
  config.vm.network :forwarded_port, guest: 50070, host: 50170
  config.vm.network :forwarded_port, guest: 50075, host: 50175
  config.vm.network :forwarded_port, guest: 50090, host: 50190
  # HBase web UI ports
  config.vm.network :forwarded_port, guest: 60010, host: 60110
  config.vm.network :forwarded_port, guest: 60030, host: 60130
  # Rest
  config.vm.network :forwarded_port, guest: 8080, host: 8180

  # increase available memory
  config.vm.provider :virtualbox do |vb|
     vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "ansible/playbook.yml"
    ansible.inventory_path = "ansible/ansible_hosts"
    ansible.limit = "all"
    ansible.verbose = "vv"
  end

end
