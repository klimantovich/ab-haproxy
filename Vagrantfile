Vagrant.configure("2") do |config|

  config.vm.define "haproxy" do |haproxy|
    haproxy.vm.box = "ubuntu/focal64"
    haproxy.vm.hostname = "haproxy.vm"
    haproxy.vm.network "private_network", ip: "10.0.5.12"

    haproxy.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "1024"
    end

    haproxy.vm.provision :ansible do |ansible|
      ansible.playbook = "./haproxy_setup.yml"
    end

  end

end

