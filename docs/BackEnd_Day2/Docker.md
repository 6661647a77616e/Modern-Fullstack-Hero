# Docker Documentation

This document provides a step-by-step guide to creating a Docker image for a Node.js application. We'll break down the Dockerfile line by line and explain its purpose.

## Prerequisites
- Docker installed on your machine. You can install Docker by following the official [Docker installation guide](https://docs.docker.com/get-docker/).

## Step 1: Create a Dockerfile

Create a file named `Dockerfile` in the root of your project directory and add the following code:

```dockerfile
# Use the official Node.js image from the Docker Hub
FROM node:20-alpine AS build

# Alpine is a minimal Docker image, making it lightweight and efficient.
# Set the working directory inside the container
WORKDIR /app 

# Copy package.json and package-lock.json to the working directory
COPY package.json package-lock.json ./

# Clean install dependencies
# This command installs the exact versions specified in package-lock.json, 
# ensuring consistency across environments and speeding up the installation.
RUN npm ci 

# Copy the entire project to the working directory
COPY . . 

# Build the application
RUN npm run build

# Expose port 4173 for the application to be accessible
EXPOSE 4173

# Define the command to run the application
CMD ["npm", "start", "preview"]
```

### Explanation of Each Line

1. **FROM node:20-alpine AS build**
   - This line specifies the base image for the Docker container. It uses Node.js version 20 on an Alpine Linux distribution, which is stripped down and lightweight, making it an efficient choice for production.

2. **WORKDIR /app**
   - This sets the working directory inside the container to `/app`. All subsequent commands will be run in this directory. If the directory does not exist, Docker will create it.

3. **COPY package.json package-lock.json ./**
   - This copies the `package.json` and `package-lock.json` files from your local machine to the container's working directory. These files are necessary for managing dependencies.

4. **RUN npm ci**
   - This command installs the exact dependencies listed in `package-lock.json`. It is faster than `npm install` because it skips the dependency resolution step and ensures that the installed versions match what was used during development.

5. **COPY . .**
   - This copies all files from your project directory on your local machine to the working directory inside the container. This includes your application code and any other necessary files.

6. **RUN npm run build**
   - This command builds the application. Typically, it compiles the source code and prepares the app for production. The specific build process depends on how your application is set up.

7. **EXPOSE 4173**
   - This line informs Docker that the container will listen on port 4173 at runtime. This is important for networking so that other services can access the application.

8. **CMD ["npm", "start", "preview"]**
   - This defines the command that will be executed when the container starts. In this case, it runs `npm start preview`, which should start your application.

## Step 2: Create a .dockerignore File

Create a file named `.dockerignore` in the root of your project directory and add the following lines:

```
.git
node_modules
.vscode
.idea
.code
```

### Explanation of .dockerignore

- **.git**
  - Excludes the `.git` directory from being copied to the Docker image, reducing its size and preventing sensitive information from being included.

- **node_modules**
  - Excludes the `node_modules` directory, which can be large and is not needed in the Docker image since dependencies will be installed during the image build process.

- **.vscode**
  - Excludes Visual Studio Code settings and configurations, which are not relevant for the container.

- **.idea**
  - Excludes JetBrains IDE configurations, similarly to `.vscode`.

- **.code**
  - Excludes any additional editor configuration files.

## Step 3: Build and Run the Docker Container

### Build the Docker Image

In your terminal, navigate to your project directory and run:

```bash
docker build -t my-node-app .
```

Replace `my-node-app` with your preferred image name.

### Run the Docker Container

After the image is built, you can run it with:

```bash
docker run -p 4173:4173 my-node-app
```

This command maps port 4173 of the container to port 4173 on your host machine, allowing you to access the application.

## Conclusion

You have now created a Docker image for your Node.js application, including all necessary steps and configurations. This Docker setup provides a consistent environment for running your application across different systems.
