# OSPF-Configuration-in-a-Single-Area-Area-0-


The provided topology consists of three routers connected in a single OSPF area (Area 0), with multiple networks connected to each router via switches and PCs. Below is a description and step-by-step guide to configure OSPF on these routers.

#### Topology Overview:
- **Routers:** Router0, Router1, Router2
- **Switches:** Switch0, Switch1, Switch2
- **PCs:** Multiple PCs connected to switches
- **OSPF Area:** Area 0

### Step-by-Step Configuration

#### Step 1: Assign IP Addresses
Assign IP addresses to each router interface as shown in the topology. Here is an example for each router:

**Router0:**
```shell
Router0> enable
Router0# configure terminal
Router0(config)# interface gigabitEthernet 0/0
Router0(config-if)# ip address 10.0.0.1 255.255.255.252
Router0(config-if)# no shutdown
Router0(config-if)# exit
Router0(config)# interface gigabitEthernet 0/1
Router0(config-if)# ip address 192.168.1.100 255.255.255.0
Router0(config-if)# no shutdown
Router0(config-if)# exit
Router0(config)# exit
```

**Router1:**
```shell
Router1> enable
Router1# configure terminal
Router1(config)# interface gigabitEthernet 0/0
Router1(config-if)# ip address 10.0.0.2 255.255.255.252
Router1(config-if)# no shutdown
Router1(config-if)# exit
Router1(config)# interface gigabitEthernet 0/1
Router1(config-if)# ip address 192.168.2.100 255.255.255.0
Router1(config-if)# no shutdown
Router1(config-if)# exit
Router1(config)# interface gigabitEthernet 0/2
Router1(config-if)# ip address 192.168.3.100 255.255.255.0
Router1(config-if)# no shutdown
Router1(config-if)# exit
Router1(config)# exit
```

**Router2:**
```shell
Router2> enable
Router2# configure terminal
Router2(config)# interface gigabitEthernet 0/0
Router2(config-if)# ip address 11.0.0.2 255.255.255.252
Router2(config-if)# no shutdown
Router2(config-if)# exit
Router2(config)# interface gigabitEthernet 0/1
Router2(config-if)# ip address 192.168.3.1 255.255.255.0
Router2(config-if)# no shutdown
Router2(config-if)# exit
Router2(config)# exit
```

#### Step 2: Configure OSPF on Routers
Enable OSPF and advertise the networks on each router.

**Router0:**
```shell
Router0> enable
Router0# configure terminal
Router0(config)# router ospf 1
Router0(config-router)# network 10.0.0.0 0.0.0.3 area 0
Router0(config-router)# network 192.168.1.0 0.0.0.255 area 0
Router0(config-router)# exit
Router0(config)# exit
```

**Router1:**
```shell
Router1> enable
Router1# configure terminal
Router1(config)# router ospf 1
Router1(config-router)# network 10.0.0.0 0.0.0.3 area 0
Router1(config-router)# network 192.168.2.0 0.0.0.255 area 0
Router1(config-router)# network 192.168.3.0 0.0.0.255 area 0
Router1(config-router)# exit
Router1(config)# exit
```

**Router2:**
```shell
Router2> enable
Router2# configure terminal
Router2(config)# router ospf 1
Router2(config-router)# network 11.0.0.0 0.0.0.3 area 0
Router2(config-router)# network 192.168.3.0 0.0.0.255 area 0
Router2(config-router)# exit
Router2(config)# exit
```

#### Step 3: Verify Configuration
Use the following commands to verify the OSPF configuration and connectivity:

**Check OSPF Neighbors:**
```shell
Router# show ip ospf neighbor
```

**Check OSPF Routes:**
```shell
Router# show ip route ospf
```

**Ping from one network to another:**
```shell
Router# ping 192.168.3.1
```

#### Step 4: Configure PCs with IP Addresses
Assign IP addresses to the PCs connected to the switches as shown in the topology.


By following these steps, you can configure the provided network topology in Cisco Packet Tracer, ensuring efficient routing and connectivity using OSPF in a single area.
