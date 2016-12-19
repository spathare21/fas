# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "fedora/25-cloud-base"
  config.vm.network "forwarded_port", guest: 6543, host: 5002
  config.vm.synced_folder ".", "/vagrant", type: "sshfs"

  # Ansible needs the guest to have these
  config.vm.provision "shell", inline: "sudo dnf install -y libselinux-python python2-dnf"

  config.vm.provision "ansible" do |ansible|
      ansible.playbook = "devel/ansible/playbook.yml"
  end

  config.vm.post_up_message = "Provisioning Complete. Start your FAS3 Server from your host with the command:\n vagrant ssh -c 'pushd /vagrant/; pserve /home/vagrant/development.ini --reload'\n Your FAS3 instance will be available at: http://localhost:5002/"

end
