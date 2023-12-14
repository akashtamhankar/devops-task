IMAGE_NAME = "ubuntu/bionic64"
N = 2

Vagrant.configure("2") do |config|
  config.vm.box = IMAGE_NAME

  config.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
  end
    
  config.vm.define "master" do |master|
    master.vm.network "private_network", ip: "192.168.56.10"
    master.vm.hostname = "master"
    master.vm.synced_folder "/home/akash/Desktop/kube", "/home/vagrant/demos"
    master.vm.provider "virtualbox" do |app|
      app.name = "master"
    end
  end

  (1..N).each do |i|
      config.vm.define "node#{i}" do |node|
        node.vm.network "private_network", ip: "192.168.56.#{i + 10}"
        node.vm.hostname = "node#{i}"
        node.vm.provider "virtualbox" do |app|
          app.name = "node#{i}"
        end 
      end
  end
end

