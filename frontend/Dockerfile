# Use the official Node.js image as the base image
FROM node:latest

# Set the working directory
WORKDIR /var/www/project

# Copy the package.json and package-lock.json files
COPY package*.json ./

# Install Angular CLI globally
RUN npm install -g @angular/cli

# Install the dependencies
RUN npm install

# Copy the Angular project files
COPY . .

# Set the working directory to the Angular app
WORKDIR /var/www/project/ecomerce-front

# Expose the port the app runs on
EXPOSE 4200
# Start the Angular application
CMD ["ng", "serve", "--host", "0.0.0.0", "--port", "4200"]