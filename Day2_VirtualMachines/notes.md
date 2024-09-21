# Day 2: Virtual Machines in Azure

## 1st Half: VM Planning & Deployment

### 1.1 Planning VM Deployments: Best Practices
- **Purpose**: Understanding the needs and the role of VMs in your infrastructure.
- **Key Considerations**:
  - Workload requirements (CPU, Memory, Storage).
  - Deployment environment (Test, Dev, Production).
  - **Scaling**: Plan for future growth.
- **Best Practices**:
  - Use the **Azure VM sizing guide** to choose the right instance type.
  - Plan **disaster recovery** strategies using Azure Backup.
  
  VM Deployment Planning

- **Further Reading**: [VM Best Practices on Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/best-practices)

---

### 1.2 Network Planning, VM Location Considerations
- **Regions & Availability Zones**:
  - Choose regions close to your users for **lower latency**.
  - Utilize **availability zones** for fault tolerance.
- **Virtual Networks (VNet)**:
  - Plan your **subnet structure** based on VM placement.
  
- **Example**: If deploying a high-availability app, distribute VMs across **multiple zones** for fault tolerance.

- **Diagram**: 
  Network Planning

---

### 1.3 Sizing VMs, VM Pricing Calculator, Disks
- **VM Sizes**: Standard, Compute Optimized, Memory Optimized, etc.
  - Example: **D-series** for general-purpose workloads, **F-series** for high CPU demand.
- **Azure Pricing Calculator**: Helps estimate costs based on the selected VM size, disks, and location.
  
  [Azure Pricing Calculator](https://azure.microsoft.com/en-us/pricing/calculator/)
  
- **Storage**: Choose between **Standard HDD**, **Premium SSD**, and **Ultra SSD** for VMs.

---

## 2nd Half: Advanced VM Concepts & Demo

### 2.1 Azure Availability Sets/Availability Zones
- **Availability Sets**: Ensures that VMs are distributed across **multiple fault domains** and **update domains**.
- **Availability Zones**: Physically separate datacenters within the same Azure region to avoid outages.
  
  Availability Sets vs Zones

- **Example**: Deploy critical applications across Availability Zones to ensure uptime.

---

### 2.2 Virtual Machine Scale Sets (VMSS)
- **What is VMSS?**: Automatically manages the number of VMs based on demand.
- **Use Cases**:
  - Web applications that need to handle **varying traffic loads**.
  - Batch processing tasks.
  
  **Key Benefits**:
  - Autoscaling based on **CPU usage** or **custom metrics**.
  - High availability with **zone redundancy**.
  
- **Further Reading**: [VM Scale Sets Documentation](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/)

---

### 2.3 Demo: Creating VMs and VM Scale Sets
- **Step-by-Step Guide**:
  1. Go to the **Azure Portal** and click **Create a Resource**.
  2. Select **Virtual Machine** and configure size, network, and disk options.
  3. Deploy the VM and connect via **SSH/RDP**.
  
  - For VMSS:
    1. Navigate to **Virtual Machine Scale Sets**.
    2. Configure **Autoscaling** based on CPU load or schedule.

  Creating VMs

---

## Additional Resources

- [Azure Virtual Machines Overview](https://docs.microsoft.com/en-us/azure/virtual-machines/)
- [VM Best Practices](https://docs.microsoft.com/en-us/azure/architecture/framework/scalability/virtual-machine-scale-sets)

