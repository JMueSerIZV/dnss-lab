Vagrant.configure("2") do |config|
    config.vm.box = "debian/bullseye64"
    config.vm.provision "ansible" do |ansible|
        ansible.inventory_path = "inventory.yaml"
    end
    config.vm.define "dns" do |dns|
        dns.vm.hostname = "dns.example.test"
        dns.vm.network "private_network", ip: "192.168.58.10"
        dns.vm.provision "ansible" do |ansible|
            ansible.playbook = "playbooks/dns.yaml"
        end
    end
    config.vm.define "dhcp" do |dhcp|
        dhcp.vm.hostname = "dhcp.example.test"
        dhcp.vm.network "private_network", ip: "192.168.58.20"
        dhcp.vm.provision "ansible" do |ansible|
            ansible.playbook = "playbooks/dhcp.yaml"
        end
    end
    config.vm.define "client" do |client|
        client.vm.hostname = "client.example.test"
        client.vm.network "private_network", type: "dhcp"
        client.vm.provision "ansible" do |ansible|
            ansible.playbook = "playbooks/client.yaml"
        end
    end
end