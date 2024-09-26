# Day 4: Load Balancing, Storage & App Services

## 1st Half: Azure Load Balancers

### 1.1 Azure Load Balancer Overview
- **Azure Load Balancer**: A Layer 4 (Transport Layer) load balancer that distributes incoming network traffic across multiple VMs.
  - **Internal vs Public Load Balancer**:
    - **Internal Load Balancer**: Routes traffic within a virtual network.
    - **Public Load Balancer**: Routes traffic from the internet to your VMs.
  
- **Traffic Distribution**:
  - Supports **round-robin**, **hash-based** distribution, and session persistence.

- **Use Case**: Distribute web traffic across multiple servers to improve reliability and redundancy.

- **Diagram**: 
  Azure Load Balancer Overview

  ![image](https://github.com/user-attachments/assets/8944dd3e-2196-43c5-84ea-9266c32761ee)


---

### 1.2 Azure Application Gateway
- **Azure Application Gateway**: A Layer 7 (Application Layer) load balancer that supports web traffic management.
  - Features include **path-based routing**, **multi-site hosting**, **SSL termination**, and **Web Application Firewall (WAF)**.
  
- **Path-Based Routing**:
  - Routes traffic to backend pools based on the URL path.
  
- **Multi-Site Hosting**:
  - Hosts multiple websites on a single Application Gateway with different listeners.

- **Use Case**: An e-commerce site hosting multiple storefronts with different URLs and security requirements.

- **Diagram**:
  Azure Application Gateway

  ![image](https://github.com/user-attachments/assets/c17d1812-00c4-44ed-bf88-7c14635347ed)


---

### 1.3 Demo: Load Balancer and Application Gateway Setup
- **Step-by-Step**:
  1. Navigate to **Azure Portal** > **Create a Resource** > **Load Balancer**.
  2. Configure **frontend IP**, **backend pool**, and **health probes** for the load balancer.
  3. Create an **Application Gateway** with multiple backend pools, listeners, and routing rules.
  
  Load Balancer Setup Demo

---

## 2nd Half: Azure Storage Overview

### 2.1 Azure Storage Services
- **Azure Blob Storage**: Object storage optimized for massive amounts of unstructured data.
  - Ideal for storing images, videos, and backups.

- **Azure Queue Storage**: Provides reliable, persistent messaging between services.

- **Azure File Storage**: Fully managed file shares accessible via SMB and NFS protocols.

- **Azure Table Storage**: A NoSQL key-value store for rapid development using structured datasets.

- **Use Case**:
  - **Blob Storage**: Store user-uploaded photos and videos.
  - **File Storage**: Share files across multiple VMs or applications.
  
- **Diagram**:
  Azure Storage Overview

---

### 2.2 Storage Tiers: Hot, Cool, Archive
- **Hot Tier**:
  - Optimized for data that is accessed frequently.
  
- **Cool Tier**:
  - Optimized for data that is infrequently accessed but requires immediate availability.

- **Archive Tier**:
  - Long-term storage for data that is rarely accessed and can tolerate several hours of retrieval time.

- **Diagram**: 
  Storage Tiers

---

### 2.3 Demo: Creating a Storage Account, Blob Containers, File Shares
- **Step-by-Step**:
  1. Navigate to **Azure Portal** > **Create a Resource** > **Storage Account**.
  2. Choose **Blob**, **File**, or **Queue** storage based on your needs.
  3. Create a **Blob container** for object storage or a **file share** for VM file sharing.
  
  Storage Account Demo

---

## Additional Resources
- [Azure Storage redundancy](https://learn.microsoft.com/en-us/azure/storage/common/storage-redundancy)
- [Access tiers for blob data](https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview_
- [Azure Load Balancer Overview](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-overview)
- [Azure Application Gateway](https://docs.microsoft.com/en-us/azure/application-gateway/overview)
- [Azure Storage Account Documentation](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview)

