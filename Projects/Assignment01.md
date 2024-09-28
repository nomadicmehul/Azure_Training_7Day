
# Project Assignment: Deploy a Web Server on Azure

## Objective

In this project, you will create a basic web server using a Virtual Machine (VM) on Microsoft Azure through the Azure portal. You will:

- Create a Resource Group.
- Set up a Virtual Network (VNet).
- Deploy a Linux Virtual Machine.
- Install a web server on the VM.
- Test the web server via a browser.

---

## Task Overview

### 1. Create a Resource Group

1. Go to the [Azure Portal](https://portal.azure.com/).
2. In the left-hand menu, click on **Resource Groups**.
3. Click **+ Create** at the top.
4. Choose your **Subscription** and enter a name for the Resource Group (e.g., `WebServerResourceGroup`).
5. Select a **Region** (e.g., `East US`) close to your location.
6. Click **Review + Create**, then click **Create**.

**Tip:**  
A resource group is a container that holds related resources for your Azure solution.

---

### 2. Create a Virtual Network (VNet)

1. In the left-hand menu, search for **Virtual networks** and select it.
2. Click **+ Create** at the top.
3. Select your subscription and the **Resource Group** you created earlier (`WebServerResourceGroup`).
4. Provide a **Name** for your VNet (e.g., `WebServerVNet`).
5. Choose a region for the VNet (e.g., `East US`).
6. Click on **IP Addresses** from the tab options at the top:
   - In the **IPv4 address space**, enter `10.0.0.0/16`.
   - In **Subnets**, click on **+ Add subnet**:
     - **Subnet name:** Enter `WebServerSubnet`.
     - **Subnet address range:** Enter `10.0.1.0/24`.
7. Click **Review + Create**, then click **Create**.

**Hint:**  
- The **address space** and **subnet** define the IP ranges for your virtual network and subnet. These can be adjusted based on your needs.

---

### 3. Create a Virtual Machine

1. In the left-hand menu, search for **Virtual Machines** and select it.
2. Click **+ Create** and choose **Azure Virtual Machine**.
3. In the **Basics** tab:
   - Select your subscription and resource group (`WebServerResourceGroup`).
   - Choose a **Virtual Machine Name** (e.g., `WebServerVM`).
   - Select your region (`East US`).
   - Under **Image**, choose **Ubuntu 20.04 LTS** (or another Linux distribution).
   - Choose a size for the VM (e.g., **Standard B1s**, which is a low-cost option).
   - Under **Administrator Account**, choose **SSH public key** for authentication.
   - Enter a username (e.g., `azureuser`).
   - If you don't already have SSH keys, click **Generate new key pair**.
4. In the **Networking** tab:
   - Under **Virtual network**, select the **WebServerVNet** you created earlier.
   - In **Subnet**, choose **WebServerSubnet**.
5. Click **Review + Create**, then click **Create**.

**Tip:**  
- Ensure you save the **SSH private key** if you generated a new key pair, as it will be used to access the VM.
- After deployment, the VM’s public IP address will be displayed. Make sure to note it down.

---

### 4. Allow HTTP Traffic (Port 80) for Web Access

1. Go back to your **Virtual Machine** (from the left-hand menu or your Resource Group).
2. Click on the **Networking** tab on the left.
3. Under **Inbound port rules**, click **Add inbound port rule**.
4. Set the following values:
   - **Destination port ranges**: `80`
   - **Protocol**: TCP
   - **Action**: Allow
   - **Name**: Allow-HTTP
5. Click **Add**.

**Hint:**  
This step ensures that your VM will allow incoming traffic on port 80, which is used for web server communication.

---

### 5. Connect to the VM and Install Apache Web Server

#### Steps to SSH into your VM:

1. Go to your **Virtual Machine** overview page in Azure.
2. Find the **Public IP address** and note it down.
3. Open a terminal on your local machine (or use an SSH client like PuTTY on Windows).
4. Use the following command to connect to the VM:

   ```bash
   ssh azureuser@<Your_VM_Public_IP>
   ```

5. Once logged in, update the package list and install Apache web server:

   ```bash
   sudo apt update
   sudo apt install apache2 -y
   ```

6. After the installation is complete, start Apache:

   ```bash
   sudo systemctl start apache2
   ```

**Tip:**  
- Replace `<Your_VM_Public_IP>` with the actual public IP address of your VM.
- To check if Apache is running, use `sudo systemctl status apache2`.

---

### 6. Test the Web Server

1. Once Apache is installed and running, open your browser and navigate to your VM's public IP address:

   ```
   http://<Your_VM_Public_IP>
   ```

2. You should see the default Apache welcome page if everything is set up correctly.

---

## Bonus: Customize Your Web Page

1. After installing Apache, navigate to the web server's root directory:

   ```bash
   cd /var/www/html
   ```

2. Edit the `index.html` file using a text editor, such as `nano`, to personalize the web page:

   ```bash
   sudo nano index.html
   ```

3. Modify the content to say something like "Welcome to My First Azure Web Server!" and save the file.

4. Reload the web page in your browser to see the changes.

---

## Clean Up Resources (Optional)

To avoid unnecessary costs, you can delete the resources once you're done with the project:

1. In the left-hand menu, select **Resource Groups**.
2. Click on the resource group (`WebServerResourceGroup`).
3. Click **Delete Resource Group** at the top.
4. Confirm the deletion by typing the resource group name.

---

## Summary

In this project, you:

- Created a Resource Group and a Virtual Network.
- Set up a Linux Virtual Machine via the Azure portal.
- Installed and configured Apache web server.
- Tested your web server by accessing it from a browser.

---

### Additional Tips

- If you need help navigating the Azure portal, refer to the [Azure Virtual Machine Documentation](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/overview).
- Double-check that your VM is running in the same region as your VNet to avoid latency issues.

---

This project will help participants understand the basics of Azure resource management, networking, and how to set up a simple web server in the cloud using the Azure portal.
