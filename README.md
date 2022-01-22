# TestNetwork
**Virtual Networks for Test 
1. Install virtualbox [https://www.virtualbox.org/]
2. install vagrant  [https://www.vagrantup.com/docs/installation]
3. Create a folder in mkdir C:\<my folder name>
4. cd \<myfolder name\>
5.  copy vagrantfile
6. In cmd  run "vagrant up"
7.  This vagrantfile creats 3 VMs in virtualbox.(Lab1,Lab2 &lab3  This 3 Vms access to Network Address Translation (NAT) which is the simplest way of accessing an external network from a virtual machine. Usually, it does not require any configuration on the host network and guest system. For this reason, it is the default networking mode in Oracle VM VirtualBox. The default gateway is 10.0.2.2. 
8. There are two internal networks (ineta and inetb). Ineta (lab1 & lab2)and inetb (lab1 & lab3) communicate through lab1. Acctually the lab1 is a router. 
9. Try to ping
               - From lab1: ping lab2 and ping lab3
               - From lab2: ping lab1 and lab3
               - From lab 3: ping lab1 and lab2
10. If there is problem, then check in lab1, cat /proc/sys/net/ipv4/ip_forward (the output must be 1)and  edit /etc/sysctl.conf and set net.ipv4.ip_forward=1.
11. aYou can check the upper by sudo sysctl -p
12. If you still can not ping then in lab2 and lab3: route del default and route add default gw \<Lab1 IP\>  \<name of nic\>              
               
