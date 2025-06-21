# Simple-Queues-Mikrotik-Bridge
Limitasi Mikrotik bridge, Simple Queues Mikrotik Bridge
```
/interface bridge
add name=bridge1
/queue simple
add max-limit=500M/500M name=Eth1 target=ether1
add max-limit=100M/100M name=Eth2 target=ether2
/interface bridge port
add bridge=bridge1 interface=sfp-sfpplus1
add bridge=bridge1 hw=no interface=ether1
add bridge=bridge1 hw=no interface=ether2
add bridge=bridge1 hw=no interface=ether3
add bridge=bridge1 hw=no interface=ether4
/interface bridge settings
set use-ip-firewall=yes
/system ntp client
set enabled=yes primary-ntp=202.162.32.12 secondary-ntp=185.125.190.58 \
    server-dns-names=8.8.8.8	
/system clock
set time-zone-name=Asia/Jakarta
/ip address
add address=103.111.222.6/28 interface=sfp-sfpplus1 network=103.111.222.0
/ip route
add distance=1 gateway=103.111.222.1

````
