# Day 6: Azure DevOps Pipelines & Jenkins

## 1st Half: Azure DevOps Pipelines

### 1.1 Introduction to Azure DevOps
- **Azure DevOps**: A set of development tools provided by Microsoft that allows you to plan, build, test, and deploy applications using CI/CD pipelines.
  - **CI/CD**: Continuous Integration (CI) and Continuous Deployment (CD) help automate the application development process by integrating code changes frequently and deploying them automatically.

- **Services in Azure DevOps**:
  - **Azure Repos**: Source code management.
  - **Azure Pipelines**: Build and release automation.
  - **Azure Boards**: Project tracking (scrum, kanban, etc.).
  - **Azure Test Plans**: Testing and quality assurance.
  - **Azure Artifacts**: Dependency management.

- **Use Case**: Automating the build, test, and deployment process for faster and reliable software delivery.

- **Diagram**: 
  Azure DevOps Overview

---

### 1.2 CI/CD Pipeline in Azure DevOps
- **Continuous Integration (CI)**:
  - Automatically build and test code each time a team member commits changes to version control.
  
- **Continuous Deployment (CD)**:
  - Automatically deploys code to production environments after passing the build and testing stages.

- **Pipeline Components**:
  - **Build Pipeline**: Defines how code is compiled and tested.
  - **Release Pipeline**: Defines how the application is deployed to different environments (staging, production).

- **Use Case**: Automating deployment to test, staging, and production environments for a microservices-based application.

- **Diagram**: 
  CI/CD Pipeline

---

### 1.3 Demo: Building and Configuring Pipelines
- **Step-by-Step Demo**:
  1. Set up an **Azure Repos** repository to store code.
  2. Create a **build pipeline**:
     - Choose the project and repository.
     - Define build tasks (build, test, package).
  3. Create a **release pipeline**:
     - Define deployment stages (e.g., dev, staging, prod).
     - Link to an artifact (output of the build).
     - Configure deployment triggers (manual or automatic).

- **Diagram**: 
  Azure Pipeline Setup
  ![image](https://github.com/user-attachments/assets/e20e2ef4-2cf1-411e-94d1-b8af7900cbb8)


---

## 2nd Half: Jenkins for Automation

### 2.1 Introduction to Jenkins
- **Jenkins**: An open-source automation server that helps automate tasks related to building, testing, and deploying applications.
  - **Jenkins Jobs**: Tasks defined to build and test code or deploy applications.
  - **Plugins**: Jenkins has a vast ecosystem of plugins that extend its capabilities (e.g., Git integration, Docker, Kubernetes).

- **Use Case**: Jenkins can integrate with Git, automate code builds, and deploy applications to servers or cloud environments.

- **Diagram**: 
  Jenkins Overview
  ![image](https://github.com/user-attachments/assets/dea1c1cf-a25f-4e01-930e-20b07053b8a8)


---

### 2.2 Setting Up Jenkins Pipelines
- **Pipelines in Jenkins**:
  - Jenkins pipelines are defined using a **Jenkinsfile** (in Groovy) and can be managed via version control.
  
- **Pipeline Stages**:
  - **Build Stage**: Compile the source code.
  - **Test Stage**: Run tests to validate code.
  - **Deploy Stage**: Deploy the application to different environments.

- **Pipeline Types**:
  - **Declarative Pipeline**: More structured, defining stages in a straightforward syntax.
  - **Scripted Pipeline**: More flexible, using Groovy scripting.

- **Diagram**: 
  Jenkins Pipeline
    ![image](https://github.com/user-attachments/assets/a2171ed9-167a-478f-aaaa-392eaf67e88d)
  
---

### 2.3 Jenkins Integration with Git/GitHub
- **Git Integration**:
  - Jenkins can be configured to trigger a build when code is committed to a Git repository.
  - Use the **Git plugin** to connect Jenkins with GitHub or any Git-based repository.

- **GitHub Webhooks**:
  - Jenkins can automatically detect changes to a repository using **webhooks** and trigger builds accordingly.

- **Use Case**: Automatically building and testing code when a pull request is opened on GitHub.

- **Diagram**: 
  Jenkins Git Integration
  ![image](https://github.com/user-attachments/assets/44e7983e-441c-4205-93f9-2a68aab1ac2d)

---

### 2.4 Demo: Creating Jenkins Pipelines and Deploying from GitHub
- **Step-by-Step Demo**:
  1. Install Jenkins and set up GitHub integration using the **Git plugin**.
  2. Create a simple **Declarative Pipeline** to pull code from a GitHub repository, build it, and deploy it to an Azure environment.
  3. Use Jenkins to automate the deployment of a Docker container from a GitHub repository.

- **Diagram**: 
  Jenkins Pipeline Demo
  ![image](https://github.com/user-attachments/assets/a2171ed9-167a-478f-aaaa-392eaf67e88d)


---

## Additional Resources

- [Azure DevOps Documentation](https://docs.microsoft.com/en-us/azure/devops/)
- [Jenkins Documentation](https://www.jenkins.io/doc/)
- [GitHub Actions](https://docs.github.com/en/actions) – as an alternative to Jenkins for CI/CD
- [Azure Pipeline Templates](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/templates)


