# Specify a base image
FROM node:alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json (if available)
COPY package.json ./

# Install project dependencies
RUN npm install

# Copy the rest of the application code
COPY ./ ./

# # Expose the port the app runs on
# EXPOSE 8080

# Default command, Define the command to run the application - Tell the image what to do when it starts as a container
CMD ["npm", "start"]