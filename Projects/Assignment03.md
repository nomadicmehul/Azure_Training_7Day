# Full-Stack Web Application Deployment with Docker, Git, and CI/CD on a Cloud Platform

## Objective

This project will test your ability to integrate various technologies and deploy a full-stack web application to a cloud platform using Docker, Git, and CI/CD pipelines. You will:

- Develop or use a simple full-stack web application (Node.js for backend, React for frontend).
- Containerize both frontend and backend using Docker.
- Push the code to GitHub.
- Set up a CI/CD pipeline using GitHub Actions or any CI/CD tool to deploy the app on a cloud platform (Azure, AWS, or GCP).
- Deploy the application using Docker Compose on a cloud platform.

---

## Task Overview

### 1. Set Up the Project Structure

1. **Initialize the Project Directory**  
   Create a directory to house both the frontend and backend code.

   ```bash
   mkdir fullstack-docker-app
   cd fullstack-docker-app
   ```

2. **Create Subdirectories for Frontend and Backend**  
   Inside the project directory, create separate folders for your frontend and backend applications.

   ```bash
   mkdir frontend backend
   ```

### 2. Develop the Frontend and Backend

- **Backend (Node.js)**: In the `backend` folder, create a simple REST API using Express.

- **Frontend (React)**: In the `frontend` folder, build a simple React app that calls your backend API.

**Hint**:  
If you’re unsure about how to structure a basic React or Node.js app, you can scaffold a project using `npx create-react-app` for React and `npm init` for Node.js.

---

### 3. Dockerize Both Frontend and Backend

1. **Create Dockerfiles for Backend and Frontend**

   **Backend Dockerfile** (`backend/Dockerfile`):

   ```dockerfile
   FROM node:14

   WORKDIR /usr/src/app
   COPY package*.json ./
   RUN npm install
   COPY . .
   EXPOSE 5000
   CMD ["npm", "start"]
   ```

   **Frontend Dockerfile** (`frontend/Dockerfile`):

   ```dockerfile
   FROM node:14

   WORKDIR /usr/src/app
   COPY package*.json ./
   RUN npm install
   COPY . .
   EXPOSE 3000
   CMD ["npm", "start"]
   ```

2. **Test Locally**

   - Build and run each container locally using Docker.

   ```bash
   docker build -t backend ./backend
   docker run -p 5000:5000 backend
   ```

   ```bash
   docker build -t frontend ./frontend
   docker run -p 3000:3000 frontend
   ```

3. **Docker Compose**

   To run both frontend and backend together, create a `docker-compose.yml` file in the project root:

   ```yaml
   version: '3'
   services:
     backend:
       build: ./backend
       ports:
         - "5000:5000"
     frontend:
       build: ./frontend
       ports:
         - "3000:3000"
   ```

4. **Test Using Docker Compose**

   Run both services using Docker Compose:

   ```bash
   docker-compose up
   ```

---

### 4. Set Up Git and Push to GitHub

1. **Initialize Git and Create a New Repository**

   ```bash
   git init
   ```

2. **Create a `.gitignore` File**

   ```bash
   echo "node_modules" > .gitignore
   ```

3. **Add All Files and Commit**

   ```bash
   git add .
   git commit -m "Initial commit"
   ```

4. **Push to GitHub**

   - Create a new repository on GitHub and push the code:

   ```bash
   git remote add origin <repository-url>
   git push -u origin master
   ```

**Tip**:  
Use branches for different features and keep your `master` branch clean.

---

### 5. CI/CD Pipeline with GitHub Actions

1. **Set Up GitHub Actions Workflow**  
   Create a `.github/workflows/deploy.yml` file to define a CI/CD pipeline:

   ```yaml
   name: CI/CD Pipeline

   on:
     push:
       branches:
         - master

   jobs:
     build-and-deploy:
       runs-on: ubuntu-latest

       steps:
       - name: Checkout code
         uses: actions/checkout@v2

       - name: Set up Docker Buildx
         uses: docker/setup-buildx-action@v1

       - name: Login to DockerHub
         uses: docker/login-action@v1
         with:
           username: ${{ secrets.DOCKER_USERNAME }}
           password: ${{ secrets.DOCKER_PASSWORD }}

       - name: Build and Push Docker Image
         run: |
           docker build -t your-dockerhub-username/backend ./backend
           docker build -t your-dockerhub-username/frontend ./frontend
           docker push your-dockerhub-username/backend
           docker push your-dockerhub-username/frontend

       - name: Deploy to Cloud (Optional)
         run: |
           # Add commands to deploy to Azure/AWS/GCP
   ```

2. **Test the Pipeline**  
   Push a change to GitHub to test if the pipeline automatically builds the Docker images and pushes them to DockerHub.

---

### 6. Cloud Deployment (Azure, AWS, GCP)

1. **Choose a Cloud Provider**  
   Set up a virtual machine on Azure.

2. **Install Docker on the VM**  
   SSH into your VM and install Docker:

   ```bash
   sudo apt-get update
   sudo apt-get install docker.io
   ```

3. **Deploy Using Docker Compose**  
   Clone the GitHub repository on your cloud VM, and then run Docker Compose to deploy the app:

   ```bash
   git clone <repository-url>
   cd fullstack-docker-app
   docker-compose up -d
   ```

4. **Access Your Application**  
   Open your browser and navigate to your VM’s public IP on the appropriate ports (e.g., `http://<VM-IP>:3000`).

---

### 7. Test Your Understanding

- Can you modify the CI/CD pipeline to automatically deploy the application to the cloud whenever changes are pushed?
- Can you add environment variables for the backend and frontend using Docker Compose?

---

## Summary

In this project, you:

- Created a full-stack web application (Node.js backend and React frontend).
- Dockerized the application using separate Dockerfiles for frontend and backend.
- Set up a GitHub repository and managed version control.
- Created a CI/CD pipeline using GitHub Actions to build and push Docker images.
- Deployed the application on a cloud platform using Docker Compose.

---
