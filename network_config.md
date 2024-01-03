# Network and Configuration
---
## Network
### Clients
#### SME
##### SME1
- Net Range: (10.0.1.0 - 10.0.1.255)/24
- Address: 10.0.1.1/24
##### SME2
- Net Range: (10.0.2.0 - 10.0.2.255)/24
- Address: 10.0.2.2/24
##### SME3
- Net Range: (10.0.3.0 - 10.0.3.255)/24
- Address: 10.0.3.3/24

---

#### LB
##### LB - VLAN10
- Net Range: (10.10.0.0 - 10.10.0.255)/24

###### LB1 - VLAN10
- Address: 10.10.0.1/24
###### LB3 - VLAN10
- Address: 10.10.0.3/24

---

##### LB - VLAN20
- Net Range: (10.20.0.0 - 10.20.0.255)/24

###### LB1 - VLAN20
- Address: 10.20.0.1/24
###### LB3 - VLAN20
- Address: 10.20.0.3/24

---

##### LB - VLAN30
- Net Range: (10.30.0.0 - 10.30.0.255)/24

###### LB1 - VLAN30
- Address: 10.30.0.1/24
###### LB3 - VLAN30
- Address: 10.30.0.3/24

---

#### LA
- Net Range: (10.2.0.0 - 10.2.255.255)/16

###### LA1
- Address: 10.2.1.1/16
###### LA2
- Address: 10.2.2.2/16
###### LA3
- Address: 10.2.3.3/16

---
---

## Lisbon

##### f0/0
- To router Aveiro
    - Address: 10.0.0.17/29

##### f0/1
- To router New York
    - Address:  10.0.0.10/29

##### f1/0
- To router RL1
    - 

#### f0 1/1
- To router RL2

---

## RL1
#### eth0
- To router Lisbon

#### eth1
- To Client LA(A2)

## RL2

#### f1/1

- To router Lisbon

#### f0/0
- To SME PoP S2

---

## Aveiro
##### f0/0
- To router Lisbon
    - Address: 10.0.0.18/29

##### f0/1
- To router Madrid
    - Address: 10.0.0.25/29
##### f1/0
- To router RA1

##### f1/1
- To router RA2


## RA1
#### eth0
- To router Aveiro

#### eth2
- To Client LA(A1)

#### eth1
- To Client LB(B1)



## RA2

#### f1/1

- To router Aveiro

#### f0/0
- To SME PoP S2

---

## New York

##### f0/0
- To router Madrid
    - Address:  10.0.0.1/29

##### f0/1
- To router Lisbon
    - Address:  10.0.0.9/29


##### f1/0
- To router RN1
    - Address: 10.0.0.17/29

## RN1

#### eth0
- To Router New York
    - Address: 10.0.0.18/29

### eth1
- To Client LB(B3)
    - VLAN10: 10.10.0.4/24
    - VLAN20: 10.20.0.4/24
    - VLAN30: 10.30.0.4/24

### eth2
- To Client LA(A3)
    - Address: 10.2.3.3/16

---

## Madrid

##### f0/0
- To router New York
    - Address:  10.0.0.2/29

##### f0/1
- To router Aveiro
    - Address: 10.0.0.26/29


##### f1/1
- To router RM1

## RM1

##### f0/0
- To client S3

#### f1/1
- To router Madrid

<!-------------------------------------------------------------------------------->


