Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  config.vm.define "ansible" do |ansible|
    ansible.vm.network "public_network", ip: "192.168.18.26"

    ansible.vm.provision "shell",
      inline: "cp /vagrant/configs/id_key /home/vagrant && chmod 600 /home/vagrant/id_key && chown vagrant:vagrant /home/vagrant/id_key"

 #   ansible.vm.provision "shell",
 #1     inline: "apt-get update && apt-get install -y software-properties-common && apt-add-repository --yes --update ppa:ansible/ansible && apt-get install -y ansible"

#     ansible.vm.provision "shell",
#       inline: "ansible-playbook -i /vagrant/configs/ansible/hosts \
#                  /vagrant/configs/ansible/playbook.yml"
  end

  config.vm.define "mysql" do |mysql|
    mysql.vm.network "public_network", ip: "192.168.18.28"
    
    mysql.vm.provision "shell",
    inline: "cat /vagrant/configs/id_key.pub >> .ssh/authorized_keys"

  end

  config.vm.define "wordpress" do |wordpress|
    wordpress.vm.network "public_network", ip: "192.168.18.30"
    
    wordpress.vm.provision "shell",
    inline: "cat /vagrant/configs/id_key.pub >> .ssh/authorized_keys"

  end

end
