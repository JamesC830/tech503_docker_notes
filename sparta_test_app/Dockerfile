# This is a copy of the Dockerfile
# in the C:\Users\jcunn\nodejs20-sparta-test-app\app folder

# Use base nodejs image (18 is the version)
FROM node:18

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package files install dependencies
COPY package*.json ./
# The * is a wildcard, so this copies package.json and package-lock.json

# Copy the rest of the application
COPY . .

# Install dependencies
RUN npm install

# Expose the port the app runs on
EXPOSE 3000

# Start the app
CMD [ "npm", "start" ]

# steps in terminal

# Navigate to sparta test app folder with the dockerfile "C:\Users\jcunn\nodejs20-sparta-test-app\app"
# docker build -t sparta-test-app .
# docker run -d -p 3000:3000 sparta-test-app

# open your browser and go to http://localhost:3000

# to stop the container
# docker stop sparta-test-app

# to delete the container (after stopping it)
# docker rm sparta-test-app
