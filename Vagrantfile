test_net="192.168.56."

MASTER="master-node-"

SLAVE="slave-node-"

DISTR="cyberdolphin_debian"

servers=[
  {
    :hostname => MASTER + "1",
    :ip => test_net + "10"
  },
  {
    :hostname => MASTER + "2",
    :ip => test_net + "20"
  },
  {
    :hostname => MASTER + "3",
    :ip => test_net + "30"
  },
  {
    :hostname => SLAVE + "1",
    :ip => test_net + "110"
  },
  {
    :hostname => SLAVE + "2",
    :ip => test_net + "120"
  },
  {
    :hostname => SLAVE + "3",
    :ip => test_net + "130"
  },
]


Vagrant.configure(2) do |config|

	config.vm.synced_folder "./data", "/vagrant"

	servers.each do |machine|

		config.vm.define machine[:hostname] do |node|
			
			node.vm.box = DISTR

			node.vm.hostname = machine[:hostname]
            
            node.vm.boot_timeout = 800
  
            node.ssh.username = "sadmin"

            node.ssh.private_key_path = "../../ssh_auto/priv_cyber_openssh"
            
            node.vm.network "private_network", ip: machine[:ip], name: "VirtualBox Host-Only Ethernet Adapter"

			node.vm.provider "virtualbox" do |vb|
				  
                                  vb.memory = "512"
  
                                  vb.cpus = 1
			end
            
		end
	end
end
