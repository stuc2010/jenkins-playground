# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  # Forward the port for Jenkins to the local host so we can use it locally but no-one else can
  config.vm.network "forwarded_port", guest: 8080, host: 58080, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 8081, host: 58081, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 8082, host: 58082, host_ip: "127.0.0.1"

  # Setup the VM so it has decent specs
  config.vm.provider "virtualbox" do |vb|
    vb.name = "jenkins_docker"
  
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
  end

  # Run the Ansible playbook to configure the machine for Docker and Jenkins
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.vault_password_file = "provisioning/vault.pass"
  end
end
