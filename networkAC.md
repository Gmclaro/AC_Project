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
| LA3    | 10.2.0.0         | 10.2.255.255             | 10.3.3.3         | 16     |

---

# Routers

## Inside Core
## NewYork
| Interface | Destination | VLAN | Subnet | Broadcast | Address | Mask |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| f0/0 | Madrid |  | 10.0.0.0 | 10.0.0.7 | 10.0.0.1 | 29 |
| f0/1 | Lisbon |  | 10.0.0.8 | 10.0.0.15 | 10.0.0.9 | 29 |
| f1/0 | RN1 |  | 10.0.0.128 | 10.0.0.135 | 10.0.0.129 | 29 |
| lo0 |  |  |  |  | 10.0.1.244 | 32 |

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
| lo0 |  |  |  |  | 10.0.1.246 | 32 |

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
| lo0 |  |  |  |  | 10.0.1.252 | 32 |


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
| lo0 |  |  |  |  | 10.0.1.248 | 32 |

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
| lo0 |  |  |  |  | 10.0.1.250 | 32 |

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
ip address 10.0.1.244 255.255.255.255
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
ip address 10.0.1.246 255.255.255.255
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

interface f1/1
ip address 10.0.0.138 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f0/0
ip address 10.0.3.2 255.255.255.0
no shutdown
exit


interface loopback0
ip address 10.0.1.252 255.255.255.255
ip ospf 1 area 0
no shutdown
exit

end
write
```

## RL2 - conf
```
configure terminal
router ospf 1
router-id 3.3.3.3
mpls ip
ip cef

interface f1/1
ip address 10.0.0.154 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f0/0
ip address 10.0.2.2 255.255.255.0
no shutdown
exit

interface loopback0
ip address 10.0.1.248 255.255.255.255
ip ospf 1 area 0
no shutdown
exit

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

interface f1/1
ip address 10.0.0.170 255.255.255.248
ip ospf 1 area 0
mpls ip
no shutdown
exit

interface f0/0
ip address 10.0.1.2 255.255.255.0
no shutdown
exit

interface loopback0
ip address 10.0.1.250 255.255.255.255
ip ospf 1 area 0
no shutdown
exit

end
write
```