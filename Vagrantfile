Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "forwarded_port", guest: 6443, host: 6443
  config.vm.provider "virtualbox" do |v|
    v.name = "k3s"
    v.memory = 4096
    v.cpus = 2
  end
  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
  config.vm.provision "shell", inline: "curl -sfL https://get.k3s.io | sh -"
end
