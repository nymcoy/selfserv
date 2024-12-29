Vagrant.configure("2") do |config|

  # Define the Server machine
  config.vm.define "server" do |server|
    server.vm.box = "debian/bookworm64"
    server.vm.network "public_network"#, bridge: "YOUR_NETWORK_INTERFACE"
    server.vm.hostname = "server"
  end 

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end

end
