Vagrant.require_version ">= 1.4.3"
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vbguest.auto_update = true

    i = 1
    config.vm.define "node#{i}" do |node|
        node.vm.box = "bento/centos-7.2"
        node.vm.provider "virtualbox" do |v|
          v.name = "node#{i}"
          v.customize ["modifyvm", :id, "--memory", "4096"]
        end
        node.vm.network :private_network, ip: "10.211.55.101"
        node.vm.hostname = "10.211.55.101"
        node.vm.provision "shell", path: "scripts/setup-centos.sh"
        node.vm.provision "shell", path: "scripts/setup-java.sh"
        node.vm.provision "shell", path: "scripts/setup-hadoop.sh"
        node.vm.provision "shell", path: "scripts/setup-hive.sh"
        node.vm.provision "shell", path: "scripts/setup-spark.sh"
        node.vm.provision "shell", path: "scripts/finalize-centos.sh"
    end
end
