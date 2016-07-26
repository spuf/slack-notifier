Vagrant.require_version ">= 1.8.4"

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  project_root = "/home/vagrant/data"

  config.vm.network "private_network", type: "dhcp"
  config.vm.synced_folder ".", project_root, type: "nfs"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 512
    vb.cpus = 1
  end

  config.vm.provision "shell", inline: <<-SHELL
    export DEBIAN_FRONTEND=noninteractive
    apt-get -q -y update
    apt-get -q -y upgrade
    apt-get -q -y install build-essential devscripts debhelper

    echo "cd #{project_root}" >> /home/vagrant/.bashrc
  SHELL

end
