Vagrant.configure("2") do |config|
  (1..3).each do |i|
    config.vm.define "node#{i}" do |node|
      node.vm.box = "cjwelle/Centos-6.7-minimal"
      node.vm.network "private_network", ip: "192.168.0.2#{i}"
      node.vm.hostname = "node#{i}.lab.com"
      node.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.customize ['createhd', '--filename', "/opt/lab/node#{i}disk2.vdi", '--variant', 'Fixed', '--size', 10 * 1024]
        v.customize ['createhd', '--filename', "/opt/lab/node#{i}disk3.vdi", '--variant', 'Fixed', '--size', 10 * 1024]
        v.customize ['storageattach', :id,  '--storagectl', 'SATA', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', "/opt/lab/node#{i}disk2.vdi"]
        v.customize ['storageattach', :id,  '--storagectl', 'SATA', '--port', 2, '--device', 0, '--type', 'hdd', '--medium', "/opt/lab/node#{i}disk3.vdi"]
      end
    end
  end
end
