Here’s a step-by-step guide for integrating Jenkins with GitHub to automate builds using Jenkins pipelines.

---

# Jenkins Integration with GitHub: Step-by-Step Guide

## Prerequisites

- Jenkins is installed and running. If you don't have it installed, you can [install Jenkins](https://www.jenkins.io/doc/book/installing/) on your local machine or a cloud server.
- A GitHub account with access to a repository.
- Jenkins has access to the internet (if running behind a firewall, you might need to configure proxy settings).

---

## Step 1: Install the Required Plugins

1. Log into your Jenkins dashboard.

2. From the Jenkins homepage, navigate to **Manage Jenkins** > **Manage Plugins**.

3. Go to the **Available** tab and search for the following plugins:
   - **Git Plugin**: Allows Jenkins to interact with Git repositories.
   - **GitHub Integration Plugin**: Provides GitHub integration features like repository scanning, webhook triggers, etc.

4. Select the plugins, then click **Install without restart** or **Install and Restart**.

---

## Step 2: Create a GitHub Personal Access Token

1. Log into your GitHub account.

2. Navigate to **Settings** > **Developer Settings** > **Personal Access Tokens**.

3. Click **Generate new token**.

4. Give the token a name (e.g., `Jenkins Integration`), select the appropriate scopes:
   - `repo`: Full control of private repositories (if working with private repos).
   - `admin:repo_hook`: Grants Jenkins the ability to configure webhooks.
   - `workflow`: Required for triggering GitHub Actions workflows (optional).

5. Generate the token and copy it somewhere safe. You will need it later for Jenkins to access your repository.

---

## Step 3: Configure Jenkins Credentials for GitHub

1. Go back to your Jenkins dashboard and navigate to **Manage Jenkins** > **Manage Credentials**.

2. Select the **Jenkins (global)** scope.

3. Click **Add Credentials**.

4. In the **Kind** dropdown, select **Secret text**.

5. Paste the GitHub Personal Access Token you copied in **Secret**.

6. Set an **ID** (e.g., `github-token`) and a **Description** (e.g., `GitHub Personal Access Token for Jenkins`).

7. Click **OK** to save.

---

## Step 4: Set Up a Jenkins Job

1. From the Jenkins dashboard, click **New Item**.

2. Enter a job name (e.g., `My GitHub Build`) and select **Freestyle project** or **Pipeline**, depending on how you'd like to structure your job. Click **OK**.

3. In the job configuration page, scroll down to the **Source Code Management** section.

4. Select **Git** as the source code management system.

5. In the **Repository URL** field, enter your GitHub repository URL (e.g., `https://github.com/username/repository.git`).

6. Under **Credentials**, select the **GitHub Token** that you created earlier (e.g., `github-token`).

7. If the repository is private, make sure the Jenkins server or agent has SSH access or is properly authenticated.

---

## Step 5: Configure the Build Triggers

1. Scroll to the **Build Triggers** section in the job configuration page.

2. Enable the **GitHub hook trigger for GITScm polling** option. This allows Jenkins to automatically trigger a build when changes are pushed to the GitHub repository.

   - You can also use the **Poll SCM** option and set a schedule for polling the repository for changes (e.g., every 5 minutes).

---

## Step 6: Configure GitHub Webhooks (Automatic Builds)

1. Go to your GitHub repository and navigate to **Settings** > **Webhooks**.

2. Click **Add webhook**.

3. In the **Payload URL** field, enter your Jenkins server URL followed by `/github-webhook/` (e.g., `http://your-jenkins-url/github-webhook/`).

4. Set the **Content type** to `application/json`.

5. Select **Just the push event** or whichever events you want Jenkins to respond to (e.g., pull request).

6. Click **Add webhook**.

This will allow GitHub to notify Jenkins when changes are made to the repository, triggering builds automatically.

---

## Step 7: Define a Build (For Freestyle Job)

1. In your Jenkins job configuration, scroll down to the **Build** section.

2. Click **Add build step** and select **Execute shell**.

3. In the command field, enter the commands to build your project. For example, if you’re using a Node.js project:

   ```bash
   npm install
   npm test
   ```

4. Save the job configuration.

---

## Step 8: Pipeline Configuration (Optional)

If you selected a **Pipeline** job, you can define your build steps directly in the pipeline script.

1. Scroll down to the **Pipeline** section.

2. Choose **Pipeline script**.

3. Use a sample Jenkins pipeline script, for example:

   ```groovy
   pipeline {
       agent any
       stages {
           stage('Checkout') {
               steps {
                   git credentialsId: 'github-token', url: 'https://github.com/username/repository.git'
               }
           }
           stage('Build') {
               steps {
                   // Example build command
                   sh 'npm install'
               }
           }
           stage('Test') {
               steps {
                   // Example test command
                   sh 'npm test'
               }
           }
       }
   }
   ```

4. Click **Save**.

---

## Step 9: Trigger and Test the Build

1. Push a commit to your GitHub repository, or manually trigger the Jenkins job by clicking **Build Now** from the job page.

2. If the GitHub webhook is set up correctly, Jenkins will trigger a build automatically whenever there is a change in the repository.

3. View the build logs by clicking on the build number in Jenkins.

---

## Step 10: Monitor and Troubleshoot

- **Webhook Delivery**: Check the status of webhook deliveries in GitHub under **Settings** > **Webhooks** > **Recent Deliveries**.
- **Build Logs**: Check the Jenkins build console for any issues if the build fails.

---

## Conclusion

You’ve successfully integrated Jenkins with GitHub, allowing you to trigger builds automatically whenever code is pushed to your repository. 
You can extend this setup to include more advanced steps, such as testing, deploying, or even integrating Docker and Kubernetes.
