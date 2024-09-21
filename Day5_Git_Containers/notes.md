# Day 5: Git & Containers

## 1st Half: Git Basics

### 1.1 Introduction to Git
- **Git**: A distributed version control system that tracks changes to files and coordinates work on those files among multiple people.
  - **Repositories (Repos)**: Storage space where your project lives.
  - **Commit**: A snapshot of changes.
  - **Branching**: Create a separate copy of your code to work on features or fixes without affecting the main branch.
  
- **Use Case**: Version controlling a software project so multiple developers can work on different features without conflicts.

- **Diagram**: 
  Git Overview

---

### 1.2 Git Configuration
- **Configuring Git**:
  - `git config --global user.name "Your Name"`
  - `git config --global user.email "your.email@example.com"`

- **Initializing a Repository**:
  - `git init` to initialize a local Git repository.
  - `git clone <repo-url>` to clone an existing remote repository.

- **Use Case**: Set up a project for version control from the start to track every change.

---

### 1.3 Git Branching and Merging
- **Branching**: Create branches to work on new features independently of the main codebase.
  - `git checkout -b <branch-name>` to create and switch to a new branch.

- **Merging**: Incorporate changes from a branch back into the main codebase.
  - `git merge <branch-name>` to merge the branch into the current branch.
  
- **Conflict Resolution**:
  - Git may prompt for manual conflict resolution if changes conflict between branches.

- **Use Case**: A team working on separate features in different branches.

- **Diagram**: 
  Git Branching

---

### 1.4 Demo: Git Commands and Conflict Resolution
- **Step-by-Step**:
  1. Create a new repository, make commits, and track changes with `git add`, `git commit`.
  2. Create and merge branches using `git checkout`, `git merge`.
  3. Handle a conflict and resolve it manually.
  
  Git Demo

---

## 2nd Half: Azure Containers & Kubernetes

### 2.1 Docker Overview
- **Docker**: A platform that allows you to automate the deployment of applications inside lightweight, portable containers.
  - **Containers**: Standardized units of software that package up code and all its dependencies.
  - **Dockerfile**: A file that contains instructions to build a Docker image.
  - **Docker Image**: A lightweight, standalone, and executable software package.
  
- **Use Case**: Consistently deploy applications in any environment (local, dev, prod).

- **Diagram**: 
  Docker Overview

---

### 2.2 Azure Container Instances (ACI)
- **Azure Container Instances (ACI)**: A PaaS service that enables you to run containers directly on Azure infrastructure without needing a full VM.
  - Supports Docker containers, Linux, and Windows-based containers.

- **Use Case**: Deploy a containerized application quickly without managing the underlying infrastructure.

- **Diagram**:
  Azure Container Instances

---

### 2.3 Kubernetes on Azure (AKS)
- **Azure Kubernetes Service (AKS)**: A managed Kubernetes service to deploy, scale, and manage containerized applications using Kubernetes.
  - Handles scaling, updating, and self-healing of the containerized applications.
  - Supports advanced networking and security configurations.
  
- **Use Case**: Deploy a microservices-based application at scale.

- **Diagram**: 
  Azure Kubernetes Service (AKS)

---

### 2.4 Demo: Deploying Containers and Setting up AKS
- **Step-by-Step**:
  1. Create a container image using a `Dockerfile` and push it to **Azure Container Registry (ACR)**.
  2. Deploy the container image to **Azure Container Instances (ACI)**.
  3. Set up a **Kubernetes cluster** using AKS and deploy the container image.
  
  AKS Demo

---

## Additional Resources

- [Git Documentation](https://git-scm.com/doc)
- [Docker Documentation](https://docs.docker.com/)
- [Azure Container Instances](https://docs.microsoft.com/en-us/azure/container-instances/)
- [Azure Kubernetes Service](https://docs.microsoft.com/en-us/azure/aks/)


