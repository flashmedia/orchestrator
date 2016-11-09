# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "boxcutter/ubuntu1604"
  config.vm.box_version = "2.0.18"

  config.vm.provider "vmware_fusion" do |v|
    v.vmx["memsize"] = "400"
    v.vmx["numvcpus"] = "1"
  end

  # set the host IP.
  host_ip = "192.168.11.22"

  # define the hostname
  config.vm.hostname = "orcdev"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: host_ip

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # If true, then any SSH connections made will enable agent forwarding.
  config.ssh.forward_agent = true

  # Share the folder between host and VM
  config.vm.synced_folder ".", "/vagrant"

  # Provision with shell, nice and simple :)

  # Fixes "stdin: is not a tty" and "mesg: ttyname failed : Inappropriate ioctl for device" messages --> mitchellh/vagrant#1673
  config.vm.provision :shell , inline: "(grep -q 'mesg n' /root/.profile && sed -i '/mesg n/d' /root/.profile && echo 'Ignore the previous error, fixing this now...') || exit 0;"

  # configuration step 0: set the host ip as an environment variable within the VM itself
  config.vm.provision "shell", inline: "echo ""export HOST_IP=#{host_ip}"" > /etc/profile.d/hostip.sh"

  # configuration step 1: provisioner
  config.vm.provision "shell", path: "vagrant/provisioner.sh"

  # configuration step 2: apt-get
  config.vm.provision "shell", path: "vagrant/apt-get.sh"

  # configuration step 3: git
  config.vm.provision "shell", path: "vagrant/git.sh"

  # configuration step 4: Docker
  config.vm.provision "shell", path: "vagrant/docker.sh"

  # configuration step 5: Docker Compose
  config.vm.provision "shell", path: "vagrant/compose.sh"

  # configuration step 6: Node.js (latest version)
  config.vm.provision "shell", path: "vagrant/nodejs.sh"

  # configuration step 7: setup environment variables
  config.vm.provision "shell", path: "vagrant/env.sh"

  # configuration step 8: install development development
  config.vm.provision "shell", path: "vagrant/development.sh"

  # configuration step 9: clean (remove unccessary data and GBs)
  config.vm.provision "shell", path: "vagrant/clean.sh"

end
