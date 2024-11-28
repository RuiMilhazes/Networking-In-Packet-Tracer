# Networking-In-Packet-Tracer

## Packet Tracer Networking Project

This project simulates a multi-building network connected by a central router. Each building has its own internal networking structure, ensuring seamless communication between devices while maintaining traffic segregation and manageability.

---

## Network Topology

### 1. Central Components
- **Central Router (R0)**:  
  Acts as the backbone of the network, connecting all five buildings.
- **WAN Links**:  
  Connect each building's router to the central router using serial or Ethernet connections.

### 2. Per Building Configuration
Each building is set up as follows:
- **Building Router (e.g., R1, R2, ...)**
    - Connects to the central router.
    - Manages communication between the central router and the building's internal network.
- **Central Switch**:
    - Connects to the building router.
    - Interconnects all floor-level switches.
- **Floor-Level Switches**:
    - One switch serves two floors.
    - Connects PCs, servers, VoIP phones, and wireless access points (WAPs) on those floors.

---

## Device Setup and IP Addressing

### 1. IP Addressing Scheme
- **Subnet Allocation**:
    - Each building is assigned its own subnet.
    - Floors within a building are further subnetted for easier management.
    - Example Subnets:
        - Building 1: 192.168. ...
            - Floor 1: 192.168. ...
            - Floor 2: 192.168. ...
        - Building 2: 192.168. ...
            - Floor 1: 192.168. ...
            - Floor 2: 192.168. ...
- **Device Addressing**:
    - **Routers**: Assigned the first usable IP in each subnet.
    - **PCs, Servers, and VoIP Phones**: Assigned static IPs within their respective subnets.
    - **WAPs**: Assigned IPs for management in the same subnet as their floor.

### 2. VLAN Configuration
- Each floor's switch is configured with VLANs to segregate traffic:
    - **VLAN 10**: Data (PCs)
    - **VLAN 20**: Voice (VoIP)
    - **VLAN 30**: Wireless (WAPs)
- Inter-VLAN routing is handled by the building router.

---

## Devices and Protocols

### 1. Devices
- **PCs**: Configured with static IPs and connected to floor switches.
- **Servers**: Deployed for file sharing, DHCP (optional), and VoIP services.
- **VoIP Phones**: Connected to switches with voice VLAN enabled.
- **Wireless Access Points (WAPs)**: Provide Wi-Fi connectivity to clients.

### 2. Protocols
- **Routing Protocol**:
    - OSPF is configured on all routers to facilitate dynamic routing.
- **Switching Protocols**:
    - VLANs for traffic segregation.
    - Trunking between switches and routers for VLAN propagation.
- **Wireless Configuration**:
    - WAPs are set with SSIDs, authentication, and encryption.
- **QoS**:
    - Quality of Service is configured on routers to prioritize VoIP traffic.

---

## Network Configuration Steps

### 1. Central Router (R0)
1. Configure interfaces to connect to building routers.
2. Enable OSPF routing and advertise connected networks.

### 2. Building Routers (R1, R2, R3, R4, R5)
1. Configure WAN interfaces for connectivity to the central router.
2. Set up LAN interfaces and subinterfaces for VLANs.
3. Enable OSPF and advertise LAN subnets.

### 3. Switch Configuration
1. Create and assign VLANs for data, voice, and wireless traffic.
2. Configure trunk links to building routers and central switches.
3. Assign ports to appropriate VLANs.

### 4. End Devices
1. Assign IPs and default gateways.
2. Configure wireless clients with SSID and security credentials.

### 5. Servers
1. Set up VoIP services (using Packet Tracer's IP Telephony settings).
2. Deploy DHCP for dynamic IP assignment (optional).

---

## Verification and Testing

### 1. Connectivity Tests
- Ping between devices on the same floor, different floors, and different buildings.
- Verify internet access (if applicable).

### 2. VLAN Functionality
- Test VLAN isolation and inter-VLAN communication via routers.

### 3. VoIP Testing
- Make test calls between VoIP phones in the network.

### 4. Wireless Testing
- Verify connectivity for wireless clients to the WAPs.

---

## Future Enhancements

### 1. Redundancy
- Implement redundant links between building routers and the central router.

### 2. Scalability
- Plan for additional buildings by extending subnets and updating OSPF configurations.

### 3. Security
- Enable ACLs on routers to filter traffic.
- Configure WPA2 or WPA3 on WAPs.
