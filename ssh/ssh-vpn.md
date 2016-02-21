# ssh-vpn
### wtf-vpn
openvpn through ssl tunnel.!

    ssh user@server -L 1194:localhost:1194

tcp-tcp :(

or

ssh socks proxy & openvpn

### man ssh

	SSH-BASED VIRTUAL PRIVATE NETWORKS
	ssh contains support for Virtual Private Network (VPN) tunnelling using the tun(4) 
	network pseudo-device, allowing two networks to be joined securely.  The sshd_config(5)
	configuration option PermitTunnel controls whether the server supports this,
	and at what level (layer 2 or 3 traffic).

	The following example would connect client network 10.0.50.0/24 with remote network
	10.0.99.0/24 using a point-to-point connection from 10.1.1.1 to 10.1.1.2,
	provided that the SSH server running on the gateway to the remote network,
	at 192.168.1.15, allows it.

	On the client:

		   # ssh -f -w 0:1 192.168.1.15 true
		   # ifconfig tun0 10.1.1.1 10.1.1.2 netmask 255.255.255.252
		   # route add 10.0.99.0/24 10.1.1.2

	On the server:

		   # ifconfig tun1 10.1.1.2 10.1.1.1 netmask 255.255.255.252
		   # route add 10.0.50.0/24 10.1.1.1

### A poor man's VPN over SSH tunnel
server:

	sysctl -w net.ipv4.ip_forward=1
	iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE
	go to client part now
	ip addr add 192.168.1.1/24 peer 192.168.1.2 dev tun0
	ip link set tun0 up
	
client:

	ssh -M -f -w 0:0 188.226.129.132 true
	go to server part now
	ip addr add 192.168.1.2/24 peer 192.168.1.1 dev tun0
	ip route add 188.226.129.132/32 via 192.168.178.1
	route add -net 0.0.0.0 netmask 0.0.0.0 dev tun0
	# ip route add 0.0.0.0/0 netmask 0.0.0.0 dev tun0
	ip route del default via 192.168.178.1 dev eth0
	
	curl icanhazip.com