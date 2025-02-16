VAGRANTFILE_API_VERSION = "2"

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "512"]
  end

  # Load Balancer
  config.vm.define "loadbalancer" do |lb|
    lb.vm.hostname = "lb"
    lb.vm.box = "ubuntu/bionic64"
    lb.vm.network "private_network", ip: "10.0.1.3"
    lb.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end

  # Application servers
  (1..2).each do |i|
    config.vm.define "app#{i}" do |app|
      app.vm.hostname = "app#{i}"
      app.vm.box = "ubuntu/bionic64"
      app.vm.network "private_network", ip: "10.0.1.#{3 + i}"
      app.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbook.yml"
      end
    end
  end

  # Database server
  config.vm.define "db" do |db|
    db.vm.hostname = "db"
    db.vm.box = "ubuntu/bionic64"
    db.vm.network "private_network", ip: "10.0.1.6"
    db.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end
end
