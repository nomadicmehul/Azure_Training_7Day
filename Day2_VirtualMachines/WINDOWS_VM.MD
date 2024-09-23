This detailed guide introduces key concepts and functionalities of the Microsoft Azure portal, along with instructions on how to navigate the platform, create a virtual machine (VM), and connect to it using Remote Desktop Protocol (RDP). Below is a summarized breakdown of the content provided:

### Microsoft Azure Portal Overview
- **Azure Portal**: A graphical user interface (GUI) to manage resources within Azure. It is browser-based and provides an easy entry point for managing cloud services compared to alternatives like the API and CLI.
- **Key Concepts**:
  - **Blade**: A contextual portion of the page that appears as you navigate.
  - **Hub**: Icons or categories on the left Azure portal menu for navigation.
  - **Journey**: A sequence of blades opened as you navigate through the portal.

### Hands-On Environment Setup
We have provided a temporary Azure environment for hands-on labs, removing the need for users to set up their own Azure account. Users are given a unique username and password to log into this environment for the duration of the lab session.

### Instructions for Using Azure Portal

#### Signing in to Azure
1. **Access the lab environment** and open the azure portal in a new browser tab.
2. Use the provided credentials (email/user and password) to log into the Azure portal.
3. Ensure you are using the environment with provided lab credentials.

### Creating a Virtual Machine (VM)
1. Navigate to the **Resource Groups** hub from the dashboard and create the resource group or use the existing resource group that created for you.
2. Begin the process of adding a new resource by selecting **+ Create**.
3. Select **Windows Server 2019 Datacenter** from the available images and configure the virtual machine with basic specifications:
   - **VM Name**: metlife-lab-vm
   - **Region**: West US
   - **Size**: B2s
   - **Credentials**: Username `student`, Password `1Metlife_Jaipur_Labs!`
4. Customize additional fields such as **OS Disk Type** (Standard SSD) and **Public inbound ports** (allow RDP on port 3389).
5. Complete the configuration and click **Review + Create** to deploy the VM. The deployment process will take about one minute.

### Navigating the Azure Portal
- The Azure portal requires multiple clicks to perform tasks. Users can pin blades to return to them quickly.
- A navigation shortcut is to click on **Microsoft Azure** in the upper left corner, which brings you back to the main dashboard.

### Additional Exploration and Learning
1. Explore features like **Security Center**, **Monitor**, and **Load Balancers**. Some features may not be accessible due to permission limits, but users can still explore what fields are required to set up resources.
2. For further learning, users can explore the Azure documentation at the provided URL.

### Connecting to the Virtual Machine (RDP)
Once the VM is up and running, you can connect to it using **Remote Desktop Protocol (RDP)**:
1. Navigate to **Virtual Machines** under Services.
2. Select the running VM (metlife-lab-vm) and click **Connect**.
3. Choose **Native RDP**, and download the RDP file.
4. Use the downloaded RDP file to establish a remote connection to the VM.

### Conclusion
This guide walked through the process of navigating the Azure portal, creating a VM, and connecting to it using RDP. It also introduced fundamental Azure concepts and encouraged exploration of additional portal functionalities, aiding users in their Azure learning journey.
