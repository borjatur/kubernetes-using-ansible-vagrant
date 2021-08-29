IMAGE_NAME = "bento/ubuntu-16.04"
WORKER_NODES = 1

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false

  config.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
  end
    
  config.vm.define "k8s-master" do |master|
      master.vm.box = IMAGE_NAME
      master.vm.network "private_network", ip: "192.168.50.10"
      master.vm.hostname = "k8s-master"
      master.vm.provision "ansible" do |ansible|
          ansible.playbook = "kubernetes-setup/master-playbook.yaml"
          ansible.extra_vars = {
            node_ip: "192.168.50.10",
          }
      end
  end

  (1..WORKER_NODES).each do |i|
      config.vm.define "node-#{i}" do |node|
          node.vm.box = IMAGE_NAME
          node.vm.network "private_network", ip: "192.168.50.#{i + 10}"
          node.vm.hostname = "node-#{i}"
          node.vm.provision "ansible" do |ansible|
              ansible.playbook = "kubernetes-setup/node-playbook.yaml"
              ansible.extra_vars = {
                  node_ip: "192.168.50.#{i + 10}",
              }
          end
      end
  end
end