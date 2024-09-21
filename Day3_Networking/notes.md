# Day 3: Networking in Azure

## 1st Half: Virtual Networks (VNet) Overview

### 1.1 Understanding Virtual Networking
- **Virtual Networks (VNet)**: The fundamental building block for your private network in Azure.
  - Enables Azure resources, such as **VMs** and **App Services**, to securely communicate with each other.
  - Provides **isolation** and **segmentation**.

- **Key Features**:
  - **Subnets**: Allows you to break the VNet into smaller sections.
  - **Network Security Groups (NSGs)**: Control inbound and outbound traffic.
  - **DNS Integration**: Custom domain support for internal communication.

- **Use Case**: You need to set up a secure, isolated network to run web apps and databases.

- **Diagram**: 
  VNet Overview

---

### 1.2 VNet Planning, VNet Peering vs VPN Gateway
- **VNet Planning**: 
  - Plan IP address ranges carefully using **CIDR notation**.
  - Use **multiple subnets** to segment traffic for different tiers (web, application, database).
  
- **VNet Peering**:
  - Enables traffic between two virtual networks, even in different regions.
  - **Low latency** and **high-speed** interconnection.
  - **Use Case**: Connecting dev and production environments.

- **VPN Gateway**:
  - Securely connects your Azure VNet to your on-premises network or other cloud providers.
  - **Use Case**: Establish a hybrid cloud environment where on-premises data centers can connect to Azure securely.

- **Diagram**: 
  VNet Peering vs VPN Gateway

---

### 1.3 Demo: VNet Peering, Creating VNets, VPN Gateway Setup
- **Step-by-Step**:
  1. Navigate to **Azure Portal** and click **Create a Resource**.
  2. Select **Virtual Network** and configure **address spaces**, **subnets**, and **security groups**.
  3. Enable **VNet Peering** to connect your networks or set up **VPN Gateway** for on-premises connectivity.
  
  Demo of VNet Peering
---

## 2nd Half: Advanced Networking

### 2.1 ExpressRoute, Gateway Transit, Cross-Subscription
- **ExpressRoute**:
  - Dedicated private connection from your data center to Azure.
  - **Faster** and more secure than a typical VPN connection.
  
- **Gateway Transit**:
  - Allows peered VNets to share a VPN or ExpressRoute gateway.
  - **Use Case**: Sharing the same VPN Gateway for multiple networks.

- **Cross-Subscription Peering**:
  - Enables connectivity across subscriptions within the same tenant.
  - **Use Case**: Multi-team/multi-department cloud environments using separate subscriptions.

- **Diagram**: 
  ExpressRoute

---

### 2.2 Filtering and Routing VNet Traffic
- **Network Security Groups (NSG)**:
  - Control **inbound** and **outbound** traffic at the subnet or NIC level.
  - Define **rules** to allow or deny traffic.
  
- **Azure Route Tables**:
  - Custom route tables to override Azure's default system routes.
  - **Use Case**: Forcing traffic through **firewalls** or **monitoring systems**.
  
- **Diagram**: 
  Filtering and Routing

---

### 2.3 Demo: Configuring ExpressRoute, Cross-VNet Communication
- **Step-by-Step Guide**:
  1. Navigate to **Azure Portal**, create an **ExpressRoute circuit**, and configure routing to your on-prem network.
  2. For **Cross-VNet communication**, configure **peering** across different subscriptions and verify traffic flows securely.

  ExpressRoute Demo

---

## Additional Resources

- [Azure Virtual Networks Overview](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)
- [VNet Peering Documentation](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview)
- [ExpressRoute Overview](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-introduction)

