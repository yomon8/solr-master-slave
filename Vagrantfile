# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  solr_servers = ["solr-master"]
  config.vm.box = "centos/7"

  (0..solr_servers.length - 1).each do |i|
    config.vm.define solr_servers[i] do | s |
      s.vm.network 'private_network', ip: "192.168.110.1#{i}"
      s.vm.hostname = solr_servers[i]
      s.vm.provider 'virtualbox' do |vb|
        vb.memory = '1024'
      end
      if i == solr_servers.length - 1
        config.vm.provision "ansible" do |ansible|
          ansible.verbose = 'v'
          ansible.playbook = "ansible/site.yml"
          ansible.inventory_path = "ansible/hosts"
          ansible.limit = 'solr_servers'
          ansible.raw_ssh_args = ['-F sshconfig']
        end
        config.vm.provision "ansible" do |ansible|
          ansible.verbose = 'v'
          ansible.playbook = "ansible/site.yml"
          ansible.inventory_path = "ansible/hosts"
          ansible.limit = 'solr_dev_env'
          ansible.raw_ssh_args = ['-F sshconfig']
        end
      end
    end
  end
end
