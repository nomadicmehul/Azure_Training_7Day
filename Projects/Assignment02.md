# Project Assignment: Dockerizing a Web Application with Git Version Control

## Objective

In this project, you will create and version control a simple web application using Git and Docker. You will:

- Initialize a Git repository for version control.
- Write a simple web application (in Node.js).
- Create a Dockerfile to containerize the application.
- Build and run the application in a Docker container.

---

## Task Overview

### 1. Set Up Your Project Directory

1. Create a new directory on your local machine for this project:

   ```bash
   mkdir docker-web-app
   cd docker-web-app
   ```

2. Initialize a new Git repository in the directory:

   ```bash
   git init
   ```

3. Create a basic `README.md` file for the project:

   ```bash
   echo "# Dockerized Web Application" > README.md
   git add README.md
   git commit -m "Initial commit with README"
   ```

**Hint:**  
Always initialize a Git repository early in the project so you can track changes from the beginning.

---

### 2. Create a Simple Web Application

For this project, we'll use **Node.js** to create a simple web application.

1. Inside the `docker-web-app` directory, create a file named `app.js` with the following content:

   ```js
   const http = require('http');

   const hostname = '0.0.0.0';
   const port = 3000;

   const server = http.createServer((req, res) => {
     res.statusCode = 200;
     res.setHeader('Content-Type', 'text/plain');
     res.end('Hello, World! This is a Dockerized web app.\n');
   });

   server.listen(port, hostname, () => {
     console.log(`Server running at http://${hostname}:${port}/`);
   });
   ```

2. Create a `package.json` file to define the project dependencies. Run the following command:

   ```bash
   npm init -y
   ```

3. Install the **http** module using npm:

   ```bash
   npm install http
   ```

4. Add all the project files to the Git repository and make a commit:

   ```bash
   git add .
   git commit -m "Added basic Node.js web app"
   ```

**Tip:**  
Make sure to include the `node_modules` folder in your `.gitignore` to avoid committing unnecessary files:

```bash
echo "node_modules" > .gitignore
```

---

### 3. Create a Dockerfile

A `Dockerfile` is a script that defines how your application is packaged inside a Docker container.

1. In your project directory, create a file named `Dockerfile` and add the following content:

   ```dockerfile
   # Use an official Node.js runtime as the base image
   FROM node:14

   # Set the working directory inside the container
   WORKDIR /usr/src/app

   # Copy package.json and package-lock.json
   COPY package*.json ./

   # Install the app dependencies inside the container
   RUN npm install

   # Copy the rest of the application code to the container
   COPY . .

   # Expose the port the app runs on
   EXPOSE 3000

   # Define the command to run the app
   CMD ["node", "app.js"]
   ```

2. Add the `Dockerfile` to your Git repository and make a commit:

   ```bash
   git add Dockerfile
   git commit -m "Added Dockerfile for Node.js app"
   ```

**Hint:**  
The Dockerfile uses a Node.js image, sets up the application in the `/usr/src/app` directory inside the container, and runs the `app.js` script.

---

### 4. Build the Docker Image

1. Open a terminal, navigate to your project directory, and build the Docker image:

   ```bash
   docker build -t docker-web-app .
   ```

2. Check if the image has been created by listing all Docker images:

   ```bash
   docker images
   ```

**Tip:**  
The `-t docker-web-app` tag names the image for easier reference later.

---

### 5. Run the Docker Container

1. Run the Docker container with the following command:

   ```bash
   docker run -p 4000:3000 docker-web-app
   ```

2. Open a browser and navigate to `http://localhost:4000`. You should see the message:

   ```
   Hello, World! This is a Dockerized web app.
   ```

**Hint:**  
The `-p 4000:3000` option maps port 4000 on your machine to port 3000 inside the container, allowing you to access the app through the browser.

---

### 6. Push the Project to GitHub

1. Create a new repository on [GitHub](https://github.com/) and copy the remote repository URL.
2. Add the remote repository to your local Git repository:

   ```bash
   git remote add origin <remote_repository_URL>
   ```

3. Push your local commits to the GitHub repository:

   ```bash
   git push -u origin master
   ```

**Tip:**  
Make sure your GitHub repository has a `.gitignore` file that ignores the `node_modules` folder.

---

### 7. Test Your Understanding

- Can you modify the `app.js` to display a personalized message or an HTML page?
- Try changing the port number inside `app.js`. What would you need to do in your Docker commands to reflect this change?

---

## Bonus: Docker Compose (Optional)

For more advanced students, introduce **Docker Compose** to manage multi-container applications (e.g., running a database alongside your app).

1. Create a `docker-compose.yml` file to define multiple services.
2. Learn how to bring up the entire environment using `docker-compose up`.

---

## Summary

In this project, you:

- Initialized a Git repository and version-controlled your project.
- Created a simple Node.js web application.
- Wrote a Dockerfile to containerize the application.
- Built and ran a Docker container to deploy your web server.
- Pushed your code to GitHub for version control and collaboration.

---

### Additional Tips

- If you need help with Docker, refer to the [Docker Documentation](https://docs.docker.com/).
- Learn more about Node.js web development from the [Node.js Documentation](https://nodejs.org/en/docs/).

---

This project gives participants hands-on experience with Git and Docker, two fundamental tools in modern software development workflows.
