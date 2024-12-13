# docker-image
This implementation guides you through setting up a Dockerfile for a Node.js project. It includes steps for creating a Dockerfile, defining the base image, working directory, copying project files, installing dependencies with Yarn, and setting the default command to run the app.


1. Prepare Your Project Directory
Ensure your Node.js project directory has:

A Dockerfile
Your application source code
Dependencies listed in package.json


Make sure you have the Docker file

If you don't have a Dockerfile, create one with the following content:

dockerfile
Copy code
# Use an official Node.js runtime as a parent image
FROM node:16

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Expose the port the app runs on
EXPOSE 3000

# Define the command to run the application
CMD ["npm", "start"]




Here’s a step-by-step guide to build and run a Docker image for your Node.js application:

1. Prepare Your Project Directory
Ensure your Node.js project directory has:

A Dockerfile
Your application source code
Dependencies listed in package.json
2. Create a Dockerfile
If you don't have a Dockerfile, create one with the following content:

dockerfile
Copy code
# Use an official Node.js runtime as a parent image
FROM node:16

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Expose the port the app runs on
EXPOSE 3000

# Define the command to run the application
CMD ["npm", "start"]


3. Build the Docker Image
Run the following command in your project directory:


Copy code
docker build -t my-node-app .
-t my-node-app: Assigns a name (my-node-app) to the image.
.: Specifies the current directory as the context.



4. Run the Docker Container
Start a container from the image with:

bash
Copy code
docker run -p 3000:3000 my-node-app
-p 3000:3000: Maps port 3000 on your host machine to port 3000 inside the container.


5. Verify the Application
Open a browser or use a tool like curl to access http://localhost:3000.
You should see your Node.js application running.


6. Stop the Container (Optional)
To stop the running container, find its CONTAINER ID using:



docker ps

Then, stop it with:


docker stop <CONTAINER ID>
