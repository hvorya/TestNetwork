Vagrant.configure("2") do |config|
            config.vm.define "lab1" do |subconfig|
                     subconfig.vm.box = "bento/ubuntu-20.04"
                     subconfig.vm.hostname="lab1"
                     #subconfig.vm.network "forwarded_port", guest: 22, host: 10001
                     subconfig.vm.network "private_network", ip: "192.168.1.1",virtualbox__intnet: true,virtualbox__intnet:"intneta"
                     subconfig.vm.network "private_network",ip: "192.168.2.1",virtualbox__intnet: true,virtualbox__intnet:"intnetb"
                     subconfig.vm.provider :virtualbox do |vb|
                                            vb.customize ["modifyvm", :id, "--memory", "4096"]
                                            vb.customize ["modifyvm", :id, "--cpus", "2"]
                     end
                     subconfig.vm.provision "shell", inline: <<-SHELL
                              sudo echo "192.168.1.3 lab2" | sudo tee -a /etc/hosts
                              sudo echo "192.168.2.3 lab3" | sudo tee -a /etc/hosts
                              sudo apt install net-tools
                              sudo apt-get install traceroute
                             sudo timedatectl set-timezone Europe/Helsinki   
                             sudo echo -e "auto eth1\niface eth1 inet static\naddress 192.168.1.1\nnetmask 255.255.255.0\nnetwork 192.168.1.0\nbroadcast 192.168.1.255\nauto eth2\niface eth2 inet static\naddress 192.168.2.1\nnetmask 255.255.255.0\nnetwork 192.168.2.0\nbroadcast 192.168.2.255" | sudo tee -a /etc/network/interfaces  
                             sudo sed -i 's/#net.ipv4.ip_forward=1/net.ipv4.ip_forward=1/g' /etc/sysctl.conf
                             sudo apt upgrade -y
                              sudo apt update
                     SHELL
                     end
               config.vm.define "lab2" do |subconfig|
                     subconfig.vm.box = "bento/ubuntu-20.04"
                     subconfig.vm.hostname="lab2"
                     #subconfig.vm.network "forwarded_port", guest: 22, host: 10002
                     subconfig.vm.network "private_network", ip: "192.168.1.3",virtualbox__intnet: true,virtualbox__intnet:"intneta" 
                     subconfig.vm.provider :virtualbox do |vb|
                                            vb.customize ["modifyvm", :id, "--memory", "4096"]
                                            vb.customize ["modifyvm", :id, "--cpus", "2"]
                     end
                     subconfig.vm.provision "shell", inline: <<-SHELL
                              sudo echo "192.168.1.1 lab1" | sudo tee -a /etc/hosts
                              sudo echo "192.168.2.3 lab3" | sudo tee -a /etc/hosts
                              sudo apt install net-tools
                              sudo apt-get install traceroute
                             sudo timedatectl set-timezone Europe/Helsinki 
                             sudo echo -e "auto eth0\niface eth0 inet dhcp\nauto eth1\niface eth1 inet static\naddress 192.168.1.3\nnetmask 255.255.255.0\nnetwork 192.168.1.0\nbroadcast 192.168.1.255\npost-up route add -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.1.1 dev eth1\npre-down route del -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.1.1 dev eth1" | sudo tee -a /etc/network/interfaces  
                             sudo apt upgrade -y 
                             sudo apt update
                     SHELL
                     end
                  config.vm.define "lab3" do |subconfig|
                     subconfig.vm.box = "bento/ubuntu-20.04"
                     subconfig.vm.hostname="lab3"
                    # subconfig.vm.network "forwarded_port", guest: 22, host: 10003
                     subconfig.vm.network "private_network",ip: "192.168.2.3",virtualbox__intnet: true,virtualbox__intnet:"intnetb"
                     subconfig.vm.provider :virtualbox do |vb|
                                            vb.customize ["modifyvm", :id, "--memory", "4096"]
                                            vb.customize ["modifyvm", :id, "--cpus", "2"]
                     end
                     subconfig.vm.provision "shell", inline: <<-SHELL
                              sudo echo "192.168.1.3 lab2" | sudo tee -a /etc/hosts
                              sudo echo "192.168.2.1 lab1" | sudo tee -a /etc/hosts
                              sudo apt install net-tools
                              sudo apt-get install traceroute
                             sudo timedatectl set-timezone Europe/Helsinki 
                             sudo echo -e "auto eth0\niface eth0 inet dhcp\nauto eth1\niface eth1 inet static\naddress 192.168.2.3\nnetmask 255.255.255.0\nnetwork 192.168.2.0\nbroadcast 192.168.2.255\npost-up route add -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.2.1 dev eth1\npre-down route del -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.2.1 dev eth1" | sudo tee -a /etc/network/interfaces 
                             sudo apt upgrade -y
                             sudo apt update
                     SHELL

         end
 end