# Day 1: Cloud Computing Basics & Azure Overview

## 1. Cloud Computing Overview

### 1.1 Introduction to Cloud Computing
Cloud computing provides scalable and flexible resources over the internet. Here's a breakdown of key concepts and models:
- **IaaS** (Infrastructure as a Service): Virtual machines, networks, storage (e.g., Azure VMs).
- **PaaS** (Platform as a Service): Application hosting services without managing infrastructure (e.g., Azure App Services).
- **SaaS** (Software as a Service): Software delivered via the cloud (e.g., Microsoft 365).

#### Key Characteristics:
- **Scalability**: Expand or shrink resources as needed.
- **Flexibility**: Access resources from anywhere.
- **Cost-effective**: Pay only for what you use.

### 1.2 Types of Clouds
There are different deployment models for cloud computing:
- **Public Cloud**: Resources hosted by a third-party provider, such as Azure Public Cloud.
- **Private Cloud**: Cloud infrastructure used exclusively by one organization.
- **Hybrid Cloud**: Combination of public and private cloud, offering more flexibility and control.

### 1.3 Cloud Pricing Models
Understanding the pricing models helps optimize costs:
- **Pay-as-you-go**: Charges based on resource usage.
- **Reserved Instances**: Pre-purchase resources for lower rates.
- **Spot Instances**: Discounts for unused capacity, ideal for short-term workloads.

---

## 2. Azure Fundamentals

### 2.1 Azure Regions & Availability Zones
Azure divides its global infrastructure into regions and Availability Zones (AZs). Each region is a collection of datacenters, while AZs are physically separated locations within a region to improve fault tolerance.

#### Diagram: Azure Regions & Availability Zones (Add Image/Diagram Here)

### 2.2 Resource Groups, Subscriptions, and Management Groups
- **Resource Groups**: Logical containers for Azure resources.
- **Subscriptions**: Billing containers grouping multiple resource groups.
- **Management Groups**: Organizational hierarchy for managing multiple subscriptions.

### 2.3 High Availability, Scalability, and Elasticity
- **High Availability**: Ensuring the application remains operational during system failures (achieved via AZs, Load Balancers).
- **Scalability**: Ability to increase or decrease resources as per demand (VM Scale Sets, Autoscaling).
- **Elasticity**: Automatically adjust resources based on the current workload.

---

## Case Study: Cloud Adoption
A small e-commerce company used to run their business on physical servers but faced scalability and availability challenges. They migrated their infrastructure to Azure using IaaS (Azure VMs) for web servers and PaaS (Azure SQL Database) for database management. This shift allowed them to handle traffic spikes effectively during sales events while reducing costs by only paying for the resources they consumed.

---

## Reference Links for Further Study
- [Azure Documentation](https://docs.microsoft.com/en-us/azure/)
- [Cloud Computing Overview by Microsoft](https://azure.microsoft.com/en-us/overview/what-is-cloud-computing/)
- [Azure Pricing Models](https://azure.microsoft.com/en-us/pricing/)
