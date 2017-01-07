# Vagrantfile
# vi: set ft=ruby :

# originally based on
# http://blog.kaliloudiaby.com/index.php/bootstrap-ci-jenkins-and-build-server-with-ansible/

Vagrant.configure("2") do |config|

  config.vm.define :jenkins_server do |jenkins_server_config|
    jenkins_server_config.vm.box               = "ubuntu/trusty64"
    jenkins_server_config.vm.hostname          = "jenkins-server"
    jenkins_server_config.vm.network             "private_network", ip: "192.168.50.200"
    jenkins_server_config.vm.synced_folder       ".", "/home/vagrant/sync", disabled: true
    jenkins_server_config.ssh.forward_agent    = true
    jenkins_server_config.ssh.insert_key       = false
    jenkins_server_config.ssh.private_key_path = [ "~/.vagrant.d/insecure_private_key" ]

    jenkins_server_config.vm.provision "ansible" do |ansible|
      ansible.playbook       = "playbook.yml"
      ansible.inventory_path = "hosts"
      ansible.limit          = "jenkins-server"

    end
  end

  config.vm.define :build_server do |build_server_config|
    build_server_config.vm.box               = "ubuntu/trusty64"
    build_server_config.vm.hostname          = "build-server"
    build_server_config.vm.network             "private_network", ip: "192.168.50.201"
    build_server_config.vm.synced_folder       ".", "/home/vagrant/sync", disabled: true
    build_server_config.ssh.forward_agent    = true
    build_server_config.ssh.insert_key       = false
    build_server_config.ssh.private_key_path = [ "~/.vagrant.d/insecure_private_key" ]

    build_server_config.vm.provision "ansible" do |ansible|
      ansible.playbook       = "playbook.yml"
      ansible.inventory_path = "hosts"
      ansible.limit          = "build-server"
    end
  end

end
