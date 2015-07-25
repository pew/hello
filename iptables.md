# iptables
## redirect port to other ip:port
redirect port 88 form server A to server B (192.168.1.128) port 88, also add the SNAT rule to get the traffic back to the source (server A, with IP 192.168.1.193)

```
iptables -t nat -A PREROUTING -p tcp --dport 88 -j DNAT --to-destination 192.168.1.128:88
iptables -t nat -A POSTROUTING -p tcp -d 192.168.1.128 --dport 88 -j SNAT --to-source 192.168.1.193
```
