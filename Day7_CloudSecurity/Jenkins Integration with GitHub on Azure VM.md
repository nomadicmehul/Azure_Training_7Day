This plan will walk through provisioning an Azure VM, installing Jenkins, and integrating it with GitHub to trigger automated builds.

---

# Jenkins Integration with GitHub on Azure VM

## Overview

The following steps will guide you through setting up Jenkins on an Azure VM and integrating it with GitHub. The main stages include:

1. Provisioning an Azure Virtual Machine (VM).
2. Installing Jenkins on the VM.
3. Configuring Jenkins with GitHub for automated builds.
4. Securing Jenkins with SSL and setting up a domain name (optional).

---

## Step 1: Create an Azure VM for Jenkins

### 1.1: Log in to Azure Portal

- Go to [Azure Portal](https://portal.azure.com) and sign in to your account.

### 1.2: Create a Virtual Machine (VM)

1. **Navigate to Virtual Machines**:
   - In the Azure portal, search for "Virtual Machines" and click **Create** > **Azure Virtual Machine**.

2. **Basic Settings**:
   - **Subscription**: Choose your subscription.
   - **Resource Group**: Create a new resource group or select an existing one.
   - **VM Name**: Give your VM a name (e.g., `Jenkins-VM`).
   - **Region**: Choose a region close to you or your audience.
   - **Image**: Select **Ubuntu Server 20.04 LTS** (for Linux).
   - **Size**: Choose a size based on your needs (e.g., `Standard_B1ms` should be sufficient for Jenkins).

3. **Administrator Account**:
   - **Authentication Type**: Choose between **SSH** or **Password**.
   - **Username**: Set a username.
   - **Password**: Set a secure password if using password authentication.
   - If using SSH, upload your public SSH key.

4. **Inbound Ports**:
   - Allow inbound ports for SSH (port 22) and HTTP (port 8080 for Jenkins).
   - You may also open port 443 for HTTPS if you're planning on securing Jenkins with SSL.

5. Click **Review + Create** and then **Create** to deploy the VM.

---

## Step 2: Connect to the Azure VM and Install Jenkins

### 2.1: Connect to the VM

1. **SSH into the VM** (for Linux-based VMs):
   - Open your terminal (Linux/macOS) or use PowerShell (Windows).
   - Run the following command (replace `<Public_IP>` with the VM's public IP):

   ```bash
   ssh <your-username>@<Public_IP>
   ```

2. **Update the package index**:

   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

### 2.2: Install Java

Jenkins requires Java, so let’s install it first.

1. Install Java Development Kit (JDK):

   ```bash
   sudo apt install openjdk-11-jdk -y
   ```

2. Verify the Java installation:

   ```bash
   java -version
   ```

You should see Java 11 installed.

### 2.3: Install Jenkins

1. Add Jenkins' official repository:

   ```bash
   wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
   sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
   ```

2. Update your package list and install Jenkins:

   ```bash
   sudo apt update
   sudo apt install jenkins -y
   ```

3. Start and enable the Jenkins service:

   ```bash
   sudo systemctl start jenkins
   sudo systemctl enable jenkins
   ```

4. Allow Jenkins through the firewall:

   ```bash
   sudo ufw allow 8080
   sudo ufw enable
   ```

---

## Step 3: Configure Jenkins

### 3.1: Access Jenkins

1. Open your browser and go to `http://<Public_IP>:8080`. You should see the Jenkins setup page.

2. **Unlock Jenkins**:
   - SSH into your VM again and run:

     ```bash
     sudo cat /var/lib/jenkins/secrets/initialAdminPassword
     ```

   - Copy the output and paste it into the Jenkins setup page.

3. **Install Suggested Plugins**:
   - Select the option to install suggested plugins. Jenkins will automatically install plugins such as the **Git Plugin**, which you'll need later.

4. **Create Admin User**:
   - Set up an admin username and password.

5. **Instance Configuration**:
   - Set your Jenkins URL (e.g., `http://<Public_IP>:8080`). You can configure this URL to use a custom domain later if needed.

6. Jenkins is now ready to use!

---

## Step 4: Install Git and Configure Jenkins Credentials

### 4.1: Install Git

1. Install Git on the VM:

   ```bash
   sudo apt install git -y
   ```

2. Verify Git installation:

   ```bash
   git --version
   ```

### 4.2: Set Up GitHub Credentials in Jenkins

1. Go to **Manage Jenkins** > **Manage Credentials**.

2. Click on **Jenkins (global)** > **Add Credentials**.

3. Select **Kind** as **Username with password** (for GitHub), and add:
   - **Username**: Your GitHub username.
   - **Password**: Your GitHub Personal Access Token (from the earlier step).

4. Click **OK** to save.

---

## Step 5: Set Up Jenkins Job with GitHub Integration

### 5.1: Create a New Jenkins Job

1. From Jenkins' dashboard, click **New Item**.

2. Choose **Freestyle project** or **Pipeline** and name the project (e.g., `GitHub-Jenkins-Integration`).

3. In the job configuration page:
   - **Source Code Management**: Select **Git** and enter the repository URL (e.g., `https://github.com/your-username/your-repository.git`).
   - **Credentials**: Select the GitHub credentials you created.

4. For **Build Triggers**, select **GitHub hook trigger for GITScm polling** to allow GitHub webhooks to trigger Jenkins builds.

---

## Step 6: Set Up GitHub Webhook

1. Go to your GitHub repository, navigate to **Settings** > **Webhooks**.

2. Click **Add Webhook**.

3. Set **Payload URL** to `http://<Public_IP>:8080/github-webhook/`.

4. Set **Content type** to `application/json` and **Trigger** for **push events**.

5. Save the webhook.

---

## Step 7: Configure Jenkins Build Pipeline

1. Add build steps for your project, such as:
   - Installing dependencies.
   - Running tests.

2. Save the job and trigger a build manually to test if everything works.

## Conclusion

Now, you have Jenkins running on an Azure VM, integrated with GitHub. You can trigger builds automatically when changes are pushed to your GitHub repository. With the optional SSL setup, your Jenkins instance will also be secured.

You can now extend this setup to include testing, deployment, and more advanced CI/CD pipelines!
