# Setting Up PM2 and Running It Automatically

## Step 1: Install PM2
First, you need to install PM2 globally using npm:
```bash
npm install pm2 -g
```

## Step 2: Start Your Application with PM2
Start your application using PM2:
```bash
pm2 start app.js
```
This only an example. Replace `app.js` with the entry point of your application and it depends on your project structure. For example, if you are using VITE react, you can use `pm2 start npm --name "vite-react" -- run dev` to start the application.

## Step 3: Save the PM2 Process List
Save the list of processes managed by PM2:
```bash
pm2 save
```

## Step 4: Configure PM2 to Start on Boot
To configure PM2 to start on boot, use the following command:
```bash
pm2 startup
```
Follow the instructions provided by the command to complete the setup.

----
---

# Adding a Run in Workflow for Docker

 If you are using Docker to deploy your application, you can add a step in your GitHub Actions workflow to build and run the Docker container.

## Step 1: Create a Dockerfile
Ensure you have a Dockerfile in your project directory:
```Dockerfile
FROM node:14
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 8080
CMD ["node", "app.js"]
```
This Dockerfile is an example for a Node.js application. Modify it according to your project requirements.

## Step 2: Create a GitHub Actions Workflow
Create a `.github/workflows/docker.yml` file with the following content:
```yaml
name: Docker CI/CD

on:
    push:
        branches:
            - main

jobs:
    build:
        runs-on: self-hosted

        steps:
        - name: Checkout code
            uses: actions/checkout@v2

        - name: Build Docker image
            run: docker build -t my-app .

        - name: Run Docker container
            run: docker run -d -p 8080:8080 --restart always my-app
```

## Step 3: Check in the Server
Ensure that the server is running and the Docker container is accessible on the specified port.

## Step 4: Run the Workflow
Push your changes to the repository to trigger the GitHub Actions workflow.

If you want to check if your Docker container is running, you can check in you server and use the following command:
```bash
docker ps
```

This workflow will build your Docker image and run it, ensuring it restarts automatically if it stops.


