# securing a server

https://ryaneschinger.com/blog/securing-a-server-with-ansible/

https://www.gnupg.org/gph/en/manual.html#AEN111

create a user
https://www.digitalocean.com/community/tutorials/automating-initial-server-setup-with-ubuntu-18-04

## ufw

https://docs.ansible.com/ansible/latest/modules/ufw_module.html
https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server

sudo ufw allow from 192.168.255.255
sudo ufw allow from 15.15.15.0/24  to any port 22


$ sudo ip link add dummy0 type dummy
$ sudo ip link set dev dummy0 up
$ ip link show type dummy
$ sudo ip addr add 169.254.1.1/32 dev dummy0 
$ sudo ip link set dev dummy0 up
$ ip addr show dev dummy0

