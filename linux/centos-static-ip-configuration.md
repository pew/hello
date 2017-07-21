# centos static ip config
## Configure eth0

	vi /etc/sysconfig/network-scripts/ifcfg-eth0

	DEVICE="eth0"
	NM_CONTROLLED="yes"
	ONBOOT=yes
	TYPE=Ethernet
	BOOTPROTO=static
	NAME="System eth0"
	IPADDR=192.168.1.2
	NETMASK=255.255.255.0


## Configure Default Gateway

	vi /etc/sysconfig/network

	NETWORKING=yes
	HOSTNAME=horst
	GATEWAY=192.168.1.1


## Restart Network Interface
	/etc/init.d/network restart

## Configure DNS Server
	
	vi /etc/resolv.conf

	nameserver 8.8.8.8
	nameserver 192.168.1.1