Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "forwarded_port", guest: 6443, host: 6443
  config.vm.provider "virtualbox" do |v|
    v.name = "k3s"
    v.memory = 4096
    v.cpus = 2
  end
  config.ssh.guest_port = 2222
  
  config.vm.provision :shell, privileged: false do |s|
    ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
    s.inline = <<-SHELL
       echo #{ssh_pub_key} >> /home/$USER/.ssh/authorized_keys
       sudo bash -c "echo #{ssh_pub_key} >> /root/.ssh/authorized_keys"
    SHELL
  end
  
  config.vm.provision "shell", inline: "curl -sfL https://get.k3s.io | sh -"
end
