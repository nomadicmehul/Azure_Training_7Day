Below is the updated step-by-step plan using **Ubuntu Server 22.04 LTS** on Azure Virtual Machine (VM) for setting up **Jenkins** integration with **GitHub**. 

# Jenkins Integration with GitHub on Azure VM

## Overview

This guide will walk through setting up Jenkins on an **Azure VM running Ubuntu Server 22.04 LTS** and integrating it with **GitHub** to trigger automated builds. You will:

1. Create an Azure Virtual Machine.
2. Install Jenkins on the VM.
3. Configure Jenkins with GitHub for automated builds.
4. Optionally set up HTTPS for Jenkins.

---

## Step 1: Create an Azure VM for Jenkins

### 1.1: Log in to Azure Portal

- Go to [Azure Portal](https://portal.azure.com) and sign in.

### 1.2: Create a Virtual Machine (VM)

1. **Navigate to Virtual Machines**:
   - In the Azure portal, search for **"Virtual Machines"** and click **Create** > **Azure Virtual Machine**.

2. **Basic Settings**:
   - **Subscription**: Choose your subscription.
   - **Resource Group**: Create a new resource group or select an existing one.
   - **VM Name**: Choose a name for your VM (e.g., `Jenkins-VM`).
   - **Region**: Select a region (closest to your location or target audience).
   - **Image**: Choose **Ubuntu Server 22.04 LTS**.
   - **Size**: Choose a size (e.g., `Standard_B1ms` should work for Jenkins).
   
3. **Administrator Account**:
   - **Authentication Type**: Select either **SSH** or **Password**.
   - **Username**: Choose a username.
   - **Password/SSH Key**: Depending on your authentication type, set the password or upload your SSH key.

4. **Inbound Ports**:
   - Allow inbound ports for SSH (port 22), HTTP (port 8080 for Jenkins).
   - You may want to open port 443 for HTTPS if you plan to secure Jenkins.

5. Click **Review + Create**, and once validated, click **Create**.

---

## Step 2: Connect to the VM and Install Jenkins

### 2.1: Connect to the VM

1. **SSH into your VM**:
   - Open your terminal or PowerShell and connect using:

   ```bash
   ssh <your-username>@<Public_IP>
   ```

2. **Update the package list**:

   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

### 2.2: Install Java

Jenkins requires Java, and Ubuntu 22.04 uses **OpenJDK 11** as the default version.

1. Install Java:

   ```bash
   sudo apt install openjdk-11-jdk -y
   ```

2. Verify Java installation:

   ```bash
   java -version
   ```

You should see Java 11 installed.

### 2.3: Install Jenkins

1. Add Jenkins’ repository and install Jenkins:

   ```bash
   curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee \
   /usr/share/keyrings/jenkins-keyring.asc > /dev/null

   echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
   https://pkg.jenkins.io/debian binary/ | sudo tee \
   /etc/apt/sources.list.d/jenkins.list > /dev/null

   sudo apt update
   sudo apt install jenkins -y
   ```

2. Start Jenkins and enable it to run at boot:

   ```bash
   sudo systemctl start jenkins
   sudo systemctl enable jenkins
   ```

3. Allow Jenkins through the firewall:

   ```bash
   sudo ufw allow 8080
   sudo ufw allow OpenSSH
   sudo ufw enable
   ```

---

## Step 3: Configure Jenkins

### 3.1: Access Jenkins

1. In your browser, go to: `http://<Public_IP>:8080`.

2. **Unlock Jenkins**:
   - SSH into your VM and use this command to find the initial admin password:

     ```bash
     sudo cat /var/lib/jenkins/secrets/initialAdminPassword
     ```

   - Copy the password and paste it into the Jenkins web interface.

3. **Install Suggested Plugins**:
   - Jenkins will prompt you to install plugins. Choose **Install suggested plugins**.

4. **Create Admin User**:
   - Set up a new admin user and complete the initial configuration.

---

## Step 4: Install Git and Configure Jenkins with GitHub

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

1. Go to **Manage Jenkins** > **Manage Credentials** > **System** > **Global Credentials**.

2. Click **Add Credentials**.
   - **Kind**: Choose **Username with password** (for GitHub).
   - **Username**: Your GitHub username.
   - **Password**: Your GitHub Personal Access Token (PAT).
   
   > To generate a PAT, go to GitHub > Settings > Developer Settings > Personal Access Tokens.

3. Click **OK** to save the credentials.

---

## Step 5: Create Jenkins Job for GitHub Integration

### 5.1: Create a New Jenkins Job

1. From the Jenkins dashboard, click **New Item**.

2. Choose **Freestyle project** or **Pipeline**. Name the project (e.g., `GitHub-Jenkins-Integration`).

3. Under **Source Code Management**, select **Git**.
   - Enter your GitHub repository URL (e.g., `https://github.com/username/repo.git`).
   - Select your GitHub credentials.

4. Under **Build Triggers**, select **GitHub hook trigger for GITScm polling**.

5. Under **Build**, add build steps such as running tests or scripts.

6. Save the job.

### 5.2: Set Up GitHub Webhook

1. Go to your GitHub repository settings.

2. Navigate to **Webhooks** > **Add Webhook**.

3. Set **Payload URL** to `http://<Public_IP>:8080/github-webhook/`.

4. Choose **Content type** as `application/json`.

5. Select the option to trigger the webhook on **push events**.

6. Save the webhook.

---

## Step 6: Test Jenkins GitHub Integration

1. Push a new commit to your GitHub repository.

2. Jenkins should trigger a build automatically.

---

## Conclusion

Now you have Jenkins set up on an **Azure VM running Ubuntu Server 22.04 LTS**, integrated with **GitHub** for automatic build triggering. You can extend this pipeline to deploy applications, run tests, or automate other tasks.

