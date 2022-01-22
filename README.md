# TestNetwork
Virtual Networks for Test 
Install virtualbox (https://www.virtualbox.org/)
install vagrant  https://www.vagrantup.com/docs/installation
mkdir C:\<my folder name>
cd <myfolder name>
  copy vagrantfile
  vagrant up
  This vagrantfile creats 3 VMs in virtualbox.(Lab1,Lab2 &lab3  This 3 Vms access to Network Address Translation (NAT) which is the simplest way of accessing an external network from a virtual machine. Usually, it does not require any configuration on the host network and guest system. For this reason, it is the default networking mode in Oracle VM VirtualBox. The default gateway is 10.0.2.2. 
  There are two internal networks (ineta and inetb). Ineta (lab1 & lab2)and inetb (lab1 & lab3) communicate through lab1. Acctually the lab1 is a router. 
