# FABRIC

## Table of Contents

- [Fabric Switches and Management IP](#fabric-switches-and-management-ip)
  - [Fabric Switches with inband Management IP](#fabric-switches-with-inband-management-ip)
- [Fabric Topology](#fabric-topology)
- [Fabric IP Allocation](#fabric-ip-allocation)
  - [Fabric Point-To-Point Links](#fabric-point-to-point-links)
  - [Point-To-Point Links Node Allocation](#point-to-point-links-node-allocation)
  - [Loopback Interfaces (BGP EVPN Peering)](#loopback-interfaces-bgp-evpn-peering)
  - [Loopback0 Interfaces Node Allocation](#loopback0-interfaces-node-allocation)
  - [VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)](#vtep-loopback-vxlan-tunnel-source-interfaces-vteps-only)
  - [VTEP Loopback Node allocation](#vtep-loopback-node-allocation)

## Fabric Switches and Management IP

| POD | Type | Node | Management IP | Platform | Provisioned in CloudVision | Serial Number |
| --- | ---- | ---- | ------------- | -------- | -------------------------- | ------------- |
| FABRIC | l3leaf | LON-LAB-ARISTA-BL01 | 192.168.104.163/24 | vEOS-lab | Provisioned | - |
| FABRIC | l3leaf | LON-LAB-ARISTA-LF01 | 192.168.104.110/24 | vEOS-lab | Provisioned | - |
| FABRIC | l3leaf | LON-LAB-ARISTA-LF02 | 192.168.104.155/24 | vEOS-lab | Provisioned | - |
| FABRIC | spine | LON-LAB-ARISTA-SPN01 | 192.168.104.164/24 | vEOS-lab | Provisioned | - |
| FABRIC | spine | LON-LAB-ARISTA-SPN02 | 192.168.104.166/24 | vEOS-lab | Provisioned | - |

> Provision status is based on Ansible inventory declaration and do not represent real status from CloudVision.

### Fabric Switches with inband Management IP

| POD | Type | Node | Management IP | Inband Interface |
| --- | ---- | ---- | ------------- | ---------------- |

## Fabric Topology

| Type | Node | Node Interface | Peer Type | Peer Node | Peer Interface |
| ---- | ---- | -------------- | --------- | ----------| -------------- |
| l3leaf | LON-LAB-ARISTA-BL01 | Ethernet49/1 | spine | LON-LAB-ARISTA-SPN01 | Ethernet9/1 |
| l3leaf | LON-LAB-ARISTA-BL01 | Ethernet50/1 | spine | LON-LAB-ARISTA-SPN02 | Ethernet9/1 |
| l3leaf | LON-LAB-ARISTA-LF01 | Ethernet49/1 | spine | LON-LAB-ARISTA-SPN01 | Ethernet1/1 |
| l3leaf | LON-LAB-ARISTA-LF01 | Ethernet50/1 | spine | LON-LAB-ARISTA-SPN02 | Ethernet1/1 |
| l3leaf | LON-LAB-ARISTA-LF02 | Ethernet49/1 | spine | LON-LAB-ARISTA-SPN01 | Ethernet2/1 |
| l3leaf | LON-LAB-ARISTA-LF02 | Ethernet50/1 | spine | LON-LAB-ARISTA-SPN02 | Ethernet2/1 |

## Fabric IP Allocation

### Fabric Point-To-Point Links

| Uplink IPv4 Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ---------------- | ------------------- | ------------------ | ------------------ |
| 10.255.255.0/26 | 64 | 12 | 18.75 % |

### Point-To-Point Links Node Allocation

| Node | Node Interface | Node IP Address | Peer Node | Peer Interface | Peer IP Address |
| ---- | -------------- | --------------- | --------- | -------------- | --------------- |
| LON-LAB-ARISTA-BL01 | Ethernet49/1 | 10.255.255.9/31 | LON-LAB-ARISTA-SPN01 | Ethernet9/1 | 10.255.255.8/31 |
| LON-LAB-ARISTA-BL01 | Ethernet50/1 | 10.255.255.11/31 | LON-LAB-ARISTA-SPN02 | Ethernet9/1 | 10.255.255.10/31 |
| LON-LAB-ARISTA-LF01 | Ethernet49/1 | 10.255.255.1/31 | LON-LAB-ARISTA-SPN01 | Ethernet1/1 | 10.255.255.0/31 |
| LON-LAB-ARISTA-LF01 | Ethernet50/1 | 10.255.255.3/31 | LON-LAB-ARISTA-SPN02 | Ethernet1/1 | 10.255.255.2/31 |
| LON-LAB-ARISTA-LF02 | Ethernet49/1 | 10.255.255.5/31 | LON-LAB-ARISTA-SPN01 | Ethernet2/1 | 10.255.255.4/31 |
| LON-LAB-ARISTA-LF02 | Ethernet50/1 | 10.255.255.7/31 | LON-LAB-ARISTA-SPN02 | Ethernet2/1 | 10.255.255.6/31 |

### Loopback Interfaces (BGP EVPN Peering)

| Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ------------- | ------------------- | ------------------ | ------------------ |
| 10.255.0.0/27 | 32 | 5 | 15.63 % |

### Loopback0 Interfaces Node Allocation

| POD | Node | Loopback0 |
| --- | ---- | --------- |
| FABRIC | LON-LAB-ARISTA-BL01 | 10.255.0.5/32 |
| FABRIC | LON-LAB-ARISTA-LF01 | 10.255.0.3/32 |
| FABRIC | LON-LAB-ARISTA-LF02 | 10.255.0.4/32 |
| FABRIC | LON-LAB-ARISTA-SPN01 | 10.255.0.1/32 |
| FABRIC | LON-LAB-ARISTA-SPN02 | 10.255.0.2/32 |

### VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)

| VTEP Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| --------------------- | ------------------- | ------------------ | ------------------ |
| 10.255.1.0/27 | 32 | 3 | 9.38 % |

### VTEP Loopback Node allocation

| POD | Node | Loopback1 |
| --- | ---- | --------- |
| FABRIC | LON-LAB-ARISTA-BL01 | 10.255.1.5/32 |
| FABRIC | LON-LAB-ARISTA-LF01 | 10.255.1.3/32 |
| FABRIC | LON-LAB-ARISTA-LF02 | 10.255.1.4/32 |
