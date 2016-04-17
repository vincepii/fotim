# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.define "mesos-master1" do |mm1|
      mm1.vm.network "public_network", ip: "192.168.0.20"
  end

  config.vm.define "mesos-master2" do |mm2|
      mm2.vm.network "public_network", ip: "192.168.0.21"
  end

  config.vm.define "mesos-master3" do |mm3|
      mm3.vm.network "public_network", ip: "192.168.0.22"
  end

  config.vm.define "mesos-slave1" do |ms1|
      ms1.vm.network "public_network", ip: "192.168.0.30"
  end

  config.vm.define "mesos-slave2" do |ms2|
      ms2.vm.network "public_network", ip: "192.168.0.31"
  end

  config.vm.define "ceph" do |ceph|
      ceph.vm.network "public_network", ip: "192.168.0.40"
  end

  # Adjust the path to your public key if not in ~/.ssh/id_rsa.pub
  config.vm.provision "shell" do |s|
    ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
    s.inline = <<-SHELL
      echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
      echo #{ssh_pub_key} >> /home/ubuntu/.ssh/authorized_keys
      echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
    SHELL
  end
end
