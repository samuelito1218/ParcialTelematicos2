Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  config.vm.define "server1" do |s1|
    s1.vm.hostname = "server1-ufw"
    s1.vm.network "private_network", ip: "192.168.50.3"
    s1.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.name = "server1-ufw"
    end
  end

  config.vm.define "server2" do |s2|
    s2.vm.hostname = "server2-ftps"
    s2.vm.network "private_network", ip: "192.168.50.2"
    s2.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.name = "server2-ftps"
    end
  end

  config.vm.define "client" do |cl|
    cl.vm.hostname = "client-linux"
    cl.vm.network "private_network", ip: "192.168.50.4"
    cl.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.name = "client-linux"
    end
  end
end
