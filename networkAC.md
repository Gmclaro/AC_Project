2024-01-03T15:23
Status: #project 
Tags: [[AC]]

# networkAC

## Map of Content
- **[[#Network]]**
	- [[#Clients]]
		1. [[#SME]]
		2. [[#LB]]
		3. [[#LA]]
	- [[#Routers]]
		- [[#Inside Core]]
			1. [[#NewYork]]
			2. [[#Madrid]]
			3. [[#Lisbon]]
			4. [[#Aveiro]]
		- [[#Outside Core]]
			1. [[#RN1]]
			2. [[#RM1]]
			3. [[#RL1]]
			4. [[#RL2]]
			5. [[#RA1]]
			6. [[#RA2]]
- **[[#Configuration]]**
	- [[#NewYork - conf]]
	- [[#Madrid - conf]]
	- [[#Lisbon - conf]]
	- [[#Aveiro - conf]]
	- [[#RM1 - conf]]
	- [[#RL2 - conf]]
	- [[#RA2 - conf]]
	-  [[#RA1-conf]]
	- [[#RA2 - conf]]
	- [[#RN1-conf]]


# Network
---
# Clients
## SME
| SME | Subnet | Broadcast | Address | Mask |
| ---- | ---- | ---- | ---- | ---- |
| SME1 | 10.0.1.0 | 10.0.1.255 | 10.0.1.1 | 24 |
| SME2 | 10.0.2.0 | 10.0.2.255 | 10.0.2.1 | 24 |
| SME3 | 10.0.3.0 | 10.0.3.255 | 10.0.3.1 | 24 |

## LB
| LB  | VLAN | Subnet    | Broadcast   | Address   | Mask |
| --- | ---- | --------- | ----------- | --------- | ---- |
| LB1 | 10   | 10.10.0.0 | 10.10.0.255 | 10.10.0.1 | 24   |
| LB1 | 20   | 10.20.0.0 | 10.20.0.255 | 10.20.0.1 | 24   |
| LB1 | 30   | 10.30.0.0 | 10.30.0.255 | 10.30.0.1 | 24   |
| LB3 | 10   | 10.10.0.0 | 10.10.0.255 | 10.10.0.3 | 24   |
| LB3 | 20   | 10.20.0.0 | 10.20.0.255 | 10.20.0.3 | 24   |
| LB3    | 30     | 10.30.0.0          | 10.30.0.255            | 10.30.0.03          | 24     |


## LA
| LA  | Subnet   | Broadcast    | Address  | Mask |
| --- | -------- | ------------ | -------- | ---- |
| LA1 | 10.2.0.0 | 10.2.255.255 | 10.2.1.1 | 16   |
| LA2 | 10.2.0.0 | 10.2.255.255 | 10.2.2.2 | 16   |
| LA3    | 10.2.0.0         | 10.2.255.255             | 10.2.3.3         | 16     |

---

# Routers

## Inside Core
## NewYork
| Interface | Destination | VLAN | Subnet | Broadcast | Address | Mask |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| f0/0 | Madrid |  | 10.0.0.0 | 10.0.0.7 | 10.0.0.1 | 29 |
| f0/1 | Lisbon |  | 10.0.0.8 | 10.0.0.15 | 10.0.0.9 | 29 |
| f1/0 | RN1 |  | 10.0.0.128 | 10.0.0.135 | 10.0.0.129 | 29 |
| lo0 |  |  |  |  | 10.0.5.244 | 32 |

## Madrid
| Interface | Destination | VLAN | Subnet | Broadcast | Address | Mask |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| f0/0 | NewYork |  | 10.0.0.0 | 10.0.0.7 | 10.0.0.2 | 29 |
| f0/1 | Aveiro |  | 10.0.0.16 | 10.0.0.23 | 10.0.0.17 | 29 |
| f1/1 | RM1 |  | 10.0.0.136 | 10.0.0.143 | 10.0.0.137 | 29 |

## Lisbon
| Interface | Destination | VLAN | Subnet | Broadcast | Address | Mask |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| f0/0 | Aveiro |  | 10.0.0.24 | 10.0.0.32 | 10.0.0.25 | 29 |
| f0/1 | NewYork |  | 10.0.0.8 | 10.0.0.15 | 10.0.0.10 | 29 |
| f1/0 | RL1 |  | 10.0.0.144 | 10.0.0.151 | 10.0.0.145 | 29 |
| f1/1 | RL2 |  | 10.0.0.152 | 10.0.0.159 | 10.0.0.153 | 29 |
| lo0 |  |  |  |  | 10.0.5.246 | 32 |

## Aveiro
| Interface | Destination | VLAN | Subnet    | Broadcast | Address   | Mask |
| --------- | ----------- | ---- | --------- | --------- | --------- | ---- |
| f0/0       | Lisbon      |      | 10.0.0.24 | 10.0.0.32 | 10.0.0.26 | 29   |
| f0/1       | Madrid     |      | 10.0.0.16  | 10.0.0.23 | 10.0.0.18 | 29   |
| f1/0          | RA1            |      | 10.0.0.160          | 10.0.0.167          | 10.0.0.161          | 29     |
| f1/1       | RA2         |      | 10.0.0.168          | 10.0.0.175          | 10.0.0.169          | 29   |

## Outside Core

## RN1
| Interface | Destination | VLAN | Subnet     | Broadcast  | Address    | Mask |
| --------- | ----------- | ---- | ---------- | ---------- | ---------- | ---- |
| eth0      | NewYork     |      | 10.0.0.128 | 10.0.0.135 | 10.0.0.130 | 29   |
| eth1      | LB3         | 10   | 10.10.0.0           | 10.10.0.255           | 10.10.0.4           | 24     |
| eth1      | LB3         | 20   | 10.20.0.0           | 10.20.0.255           | 10.20.0.4           | 24     |
| eth1      | LB3         | 30   | 10.30.0.0           | 10.30.0.255           | 10.30.0.4           | 24     |
| eth2      | LA3         |      | 10.2.0.0           | 10.2.255.255           | 10.2.3.4           | 16     |

## RM1
| Interface | Destination | VLAN | Subnet | Broadcast | Address | Mask |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| f1/1 | Madrid |  | 10.0.0.136 | 10.0.0.143 | 10.0.0.138 | 29 |
| f0/0 | S3 |  | 10.0.3.0 | 10.0.3.255 | 10.0.3.2 | 24 |
| lo0 |  |  |  |  | 10.0.5.252 | 32 |


## RL1
| Interface | Destination | VLAN | Subnet | Broadcast | Address | Mask |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| eth0 | Lisbon |  | 10.0.0.144 | 10.0.0.151 | 10.0.0.136 | 29 |
| eth1 | LA2 |  | 10.2.0.0 | 10.2.255.255 | 10.2.2.4 | 16 |

## RL2
| Interface | Destination | VLAN | Subnet | Broadcast | Address | Mask |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| f1/1 | Lisbon |  | 10.0.0.152 | 10.0.0.159 | 10.0.0.154 | 29 |
| f0/0 | S2 |  | 10.0.2.0 | 10.0.2.255 | 10.0.2.2 | 24 |
| lo0 |  |  |  |  | 10.0.5.248 | 32 |

## RA1
| Interface | Destination | VLAN | Subnet     | Broadcast  | Address    | Mask |
| --------- | ----------- | ---- | ---------- | ---------- | ---------- | ---- |
| eth0      | Aveiro      |      | 10.0.0.160 | 10.0.0.167 | 10.0.0.162 | 29   |
| eth1      | LB1         | 10   | 10.10.0.0  | 10.10.0.255           | 10.10.0.2           | 24     |
| eth1      | LB1         | 20   | 10.20.0.0           | 10.20.0.255           | 10.20.0.2           | 24     |
| eth1      | LB1         | 30   | 10.30.0.0           | 10.30.0.255           | 10.30.0.2           | 24     |
| eth2      | LA1         |      | 10.2.0.0           | 10.2.255.255           | 10.2.1.4           | 16     |

## RA2
| Interface | Destination | VLAN | Subnet | Broadcast | Address | Mask |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| f1/1 | Aveiro |  | 10.0.0.168 | 10.0.0.175 | 10.0.0.170 | 29 |
| f0/0 | S1 |  | 10.0.1.0 | 10.0.1.255 | 10.0.1.2 | 24 |
| lo0 |  |  |  |  | 10.0.5.250 | 32 |

---
# Configuration

## NewYork - conf

```
!NewYork
configure terminal
mpls ip
router ospf 1
router-id 1.1.1.1
ip cef

interface f0/0
ip address 10.0.0.1 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f0/1
ip address 10.0.0.9 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f1/0
ip address 10.0.0.129 255.255.255.248
ip ospf 1 area 0
no shutdown
mpls ip
exit

interface loopback0
ip address 10.0.5.244 255.255.255.255
ip ospf 1 area 0
no shutdown
exit

end
write
```

## Madrid - conf
```
!Madrid
configure terminal
router ospf 1
router-id 1.1.1.2
mpls ip
ip cef

interface f0/0
ip address 10.0.0.2 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f0/1
ip address 10.0.0.17 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f1/1
ip address 10.0.0.137 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

end
write
```

## Lisbon - conf
```
!Lisbon
configure terminal
router ospf 1
router-id 1.1.1.3
mpls ip
ip cef


interface f0/0
ip address 10.0.0.25 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f0/1
ip address  10.0.0.10 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f1/0
ip address 10.0.0.145 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f1/1
ip address 10.0.0.153 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface loopback0
ip address 10.0.5.246 255.255.255.255
ip ospf 1 area 0
no shutdown
exit

end
write
```

## Aveiro - conf
```
!Aveiro
configure terminal
router ospf 1
router-id 1.1.1.4
mpls ip
ip cef

interface f0/0
ip address 10.0.0.26 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f0/1
ip address 10.0.0.18 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f1/0
ip address 10.0.0.161 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f1/1
ip address 10.0.0.169 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

end
write
```

## RM1 - conf
```
!RM1
configure terminal
router ospf 1
router-id 2.2.2.2
mpls ip
ip cef

ip vrf VPN-1
rd 200:1
route-target export 200:1
route-target import 200:1
exit

interface f1/1
ip address 10.0.0.138 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f0/0
ip address 10.0.3.2 255.255.255.0
no shutdown
ip vrf forwarding VPN-1
ip address 10.0.3.2 255.255.255.0
exit


interface loopback0
ip address 10.0.5.252 255.255.255.255
ip ospf 1 area 0
no shutdown
exit

router bgp 33900
bgp router-id 10.10.10.10
neighbor 10.0.5.248 remote-as 33900
neighbor 10.0.5.248 update-source loopback0
neighbor 10.0.5.250 remote-as 33900
neighbor 10.0.5.250 update-source loopback0
address-family vpnv4
neighbor 10.0.5.248 activate
neighbor 10.0.5.248 send-community both
neighbor 10.0.5.250 activate
neighbor 10.0.5.250 send-community both
exit
address-family ipv4 vrf VPN-1
redistribute connected

end
write
```

## RL2 - conf
```
!RL2
configure terminal
router ospf 1
router-id 3.3.3.3
mpls ip
ip cef

ip vrf VPN-1
rd 200:1
route-target export 200:1
route-target import 200:1
exit

interface f1/1
ip address 10.0.0.154 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f0/0
ip address 10.0.2.2 255.255.255.0
no shutdown
ip vrf forwarding VPN-1
ip address 10.0.2.2 255.255.255.0
exit

interface loopback0
ip address 10.0.5.248 255.255.255.255
ip ospf 1 area 0
no shutdown
exit

router bgp 33900
bgp router-id 10.10.10.11
neighbor 10.0.5.252 remote-as 33900
neighbor 10.0.5.252 update-source loopback0
neighbor 10.0.5.250 remote-as 33900
neighbor 10.0.5.250 update-source loopback0
address-family vpnv4
neighbor 10.0.5.252 activate
neighbor 10.0.5.252 send-community both
neighbor 10.0.5.250 activate
neighbor 10.0.5.250 send-community both
exit
address-family ipv4 vrf VPN-1
redistribute connected

end
write
```

## RA2 - conf
```
!RA2
configure terminal
router ospf 1
router-id 4.4.4.4
mpls ip
ip cef

ip vrf VPN-1
rd 200:1
route-target export 200:1
route-target import 200:1
exit

interface f1/1
ip address 10.0.0.170 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f0/0
ip address 10.0.1.2 255.255.255.0
no shutdown
ip vrf forwarding VPN-1
ip address 10.0.1.2 255.255.255.0
exit

interface loopback0
ip address 10.0.5.250 255.255.255.255
ip ospf 1 area 0
no shutdown
exit

router bgp 33900
bgp router-id 10.10.10.12
neighbor 10.0.5.252 remote-as 33900
neighbor 10.0.5.252 update-source loopback0
neighbor 10.0.5.248 remote-as 33900
neighbor 10.0.5.248 update-source loopback0
address-family vpnv4
neighbor 10.0.5.252 activate
neighbor 10.0.5.252 send-community both
neighbor 10.0.5.248 activate
neighbor 10.0.5.248 send-community both
exit
address-family ipv4 vrf VPN-1
redistribute connected

end
write
```

## RL1- conf
```
sudo cp /opt/vyatta/etc/config.boot.default /config/config.boot
reboot

configure
set interfaces ethernet eth1 address 10.0.0.136/26
set interfaces dummy dum0 address 10.0.1.212/32 -> dummy
set protocols ospf area 0 network 10.0.0.128/26 ->defines o que queres
set protocols ospf area 0 network 10.0.1.212/32-> dummy
set system host-name RL1

set protocols bgp system-as 33900

set protocols bgp address-family l2vpn-evpn advertise-all-vni
set protocols bgp parameters router-id 10.0.1.212 ->dummy
set protocols bgp neighbor 10.0.1.208 peer-group evpn
set protocols bgp peer-group evpn update-source dum0
set protocols bgp peer-group evpn remote-as 33900
set protocols bgp peer-group evpn address-family l2vpn-evpn nexthop-self

set interfaces vxlan vxlan101 source-address 10.0.1.212
set interfaces vxlan vxlan101 vni 101
set interfaces vxlan vxlan101 mtu 1500

set interfaces bridge br101 address 10.2.3.1/22
set interfaces bridge br101 description 'client la2'
set interfaces bridge br101 member interface eth1
set interfaces bridge br101 member interface vxlan101

commit
save
```

## RA1- conf

```
VyOS2 - AVEIRO


sudo cp /opt/vyatta/etc/config.boot.default /config/config.boot
reboot

configure
set interfaces ethernet eth0 address 10.0.0.162/29
set interfaces dummy dum0 address 10.0.1.212/32 -> nao depende do loopback mas tem que ser mascara 32
set protocols ospf area 0 network 10.0.0.128/26-> defines o que queres
set protocols ospf area 0 network 10.0.1.212/32 -> ja se sabe
set system host-name RA1

set interfaces ethernet eth1 vif 10
set interfaces ethernet eth1 vif 20
set interfaces ethernet eth1 vif 30

set protocols bgp system-as 33900

set protocols bgp address-family l2vpn-evpn advertise-all-vni
set protocols bgp parameters router-id 10.0.1.212-> dummy
set protocols bgp neighbor 10.0.1.208 peer-group evpn -> mesmo que os outros vyos
set protocols bgp peer-group evpn update-source dum0
set protocols bgp peer-group evpn remote-as 33900
set protocols bgp peer-group evpn address-family l2vpn-evpn nexthop-self
set protocols bgp peer-group evpn address-family l2vpn-evpn route-reflector-client

set interfaces vxlan vxlan101 source-address 10.0.1.212->dummy
set interfaces vxlan vxlan101 vni 101
set interfaces vxlan vxlan101 mtu 1500

set interfaces vxlan vxlan110 vni 110
set interfaces vxlan vxlan110 mtu 1500
set interfaces vxlan vxlan110 remote 10.0.0.66 -> mudar estes ips
set interfaces vxlan vxlan120 vni 120
set interfaces vxlan vxlan120 mtu 1500
set interfaces vxlan vxlan120 remote 10.0.0.66 -> mudar estes ips
set interfaces vxlan vxlan130 vni 130
set interfaces vxlan vxlan130 mtu 1500
set interfaces vxlan vxlan130 remote 10.0.0.66 -> mudar estes ips

set interfaces bridge br101 address 10.2.3.1/22 -> mudar estes ips
set interfaces bridge br101 description 'client la1'
set interfaces bridge br101 member interface eth2
set interfaces bridge br101 member interface vxlan101

set interfaces bridge br110 member interface eth1.10
set interfaces bridge br110 member interface vxlan110
set interfaces bridge br120 member interface eth1.20
set interfaces bridge br120 member interface vxlan120
set interfaces bridge br130 member interface eth1.30
set interfaces bridge br130 member interface vxlan130

commit
save
```


## RN1 - conf

```
Vyos2- New york

sudo cp /opt/vyatta/etc/config.boot.default /config/config.boot
reboot

configure
set interfaces ethernet eth0 address 10.0.0.130/29
set interfaces dummy dum0 address 10.0.1.212/32 -> nao depende do loopback mas tem que ser mascara 32
set protocols ospf area 0 network 10.0.0.128/26-> defines o que queres
set protocols ospf area 0 network 10.0.1.212/32 -> ja se sabe
set system host-name RN1

set interfaces ethernet eth1 vif 10
set interfaces ethernet eth1 vif 20
set interfaces ethernet eth1 vif 30

set protocols bgp system-as 33900

set protocols bgp address-family l2vpn-evpn advertise-all-vni
set protocols bgp parameters router-id 10.0.1.212-> dummy
set protocols bgp neighbor 10.0.1.208 peer-group evpn -> mesmo que os outros vyos
set protocols bgp peer-group evpn update-source dum0
set protocols bgp peer-group evpn remote-as 33900
set protocols bgp peer-group evpn address-family l2vpn-evpn nexthop-self

set interfaces vxlan vxlan101 source-address 10.0.1.212->dummy
set interfaces vxlan vxlan101 vni 101
set interfaces vxlan vxlan101 mtu 1500

set interfaces vxlan vxlan110 vni 110
set interfaces vxlan vxlan110 mtu 1500
set interfaces vxlan vxlan110 remote 10.0.0.66 -> mudar estes ips
set interfaces vxlan vxlan120 vni 120
set interfaces vxlan vxlan120 mtu 1500
set interfaces vxlan vxlan120 remote 10.0.0.66 -> mudar estes ips
set interfaces vxlan vxlan130 vni 130
set interfaces vxlan vxlan130 mtu 1500
set interfaces vxlan vxlan130 remote 10.0.0.66 -> mudar estes ips

set interfaces bridge br101 address 10.2.3.1/22 -> mudar estes ips
set interfaces bridge br101 description 'client la3'
set interfaces bridge br101 member interface eth2
set interfaces bridge br101 member interface vxlan101

set interfaces bridge br110 member interface eth1.10
set interfaces bridge br110 member interface vxlan110
set interfaces bridge br120 member interface eth1.20
set interfaces bridge br120 member interface vxlan120
set interfaces bridge br130 member interface eth1.30
set interfaces bridge br130 member interface vxlan130

commit
save
```