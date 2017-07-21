# install openvpn server
... with certificate authentication

## installation
on ubuntu or debian:

```
apt-get install openvpn easy-rsa
```

## configuration

get sample configuration (ubuntu)

```
gunzip -c /usr/share/doc/openvpn/examples/sample-config-files/server.conf.gz > /etc/openvpn/server.conf
```

read through documentation for anything interesting or chnage the following

```
dh dh2048.pem
push "redirect-gateway def1 bypass-dhcp" # to route web traffic, maybe not needed
push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"
user nobody
group nogroup
```

packet forwarding on linux:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

add the following to `/etc/sysctl.conf` to make ip forwarding persistent:

```
net.ipv4.ip_forward=1
```

configure ufw firewall (if used)

```
ufw allow 1194/udp
```

check ufw forward policy:

```
vim /etc/default/ufw
```

```
DEFAULT_FORWARD_POLICY="ACCEPT"
```

UFW nat policy

```
vim /etc/ufw/before.rules
```

put the following BEFORE the filter part. so, place it on the beginning of the file:

```
# START OPENVPN RULES
# NAT table rules
*nat
:POSTROUTING ACCEPT [0:0] 
# Allow traffic from OpenVPN client to eth0
-A POSTROUTING -s 10.8.0.0/8 -o eth0 -j MASQUERADE
COMMIT
# END OPENVPN RULES
```

before this, k?:

```
# Don't delete these required lines, otherwise there will be errors
*filter
```

## easy-rsa

become your own ca and generate certificates for authentication

```
openssl dhparam -out /etc/openvpn/dh2048.pem 2048
cp -r /usr/share/easy-rsa/ /etc/openvpn
mkdir /etc/openvpn/easy-rsa/keys
export KEY_NAME="server"
cd /etc/openvpn/easy-rsa
. ./vars
./clean-all
./build-ca
./build-key-server server
cp /etc/openvpn/easy-rsa/keys/{server.crt,server.key,ca.crt} /etc/openvpn
./build-key client1
```

## create client configuration

```
root@hello:/etc/openvpn/easy-rsa# vim keys/client.ovpn
```

```
client
remote myserver.com 1194
proto udp
dev tun
persist-key
persist-tun
resolv-retry infinite
nobind
comp-lzo
verb 3
<ca>
INSERT CONTENT OF CA.CRT HERE
</ca>
<cert>
INSERT CONTENT OF CLIENT.CRT HERE
</cert>
<key>
INSERT CONTENT OF CLIENT.KEY HERE
</key>
```

# troubleshooting
## all clients get the same IP address
... because you are using the same client certificate on every machine? bad. but... you can also change the server configuration:

```
duplicate-cn
```

## client's can't talk to each other
... enable client-to-client in server configuration

```
client-to-client
```

# configs

## server config

without traffic redirection! to route traffic trough the VPN as well, add the following line:

```
push "redirect-gateway def1 bypass-dhcp"
```

server.conf

```
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 10.8.0.0 255.255.255.0"
push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"
client-to-client
duplicate-cn
keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
```

## client config

```
client
remote super.duper.domain.awesome.geek 1194
proto udp
dev tun
persist-key
persist-tun
resolv-retry infinite
nobind
comp-lzo
verb 3
<ca>
-----BEGIN CERTIFICATE-----
b8G1tveL
-----END CERTIFICATE-----
</ca>
<cert>
-----BEGIN CERTIFICATE-----
-----END CERTIFICATE-----
</cert>
<key>
-----BEGIN PRIVATE KEY-----
-----END PRIVATE KEY-----
</key>
```