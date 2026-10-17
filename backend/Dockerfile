# Use a Node.js base image. You should use the node:18-alpine image.
FROM node:18-alpine

# Set a working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json files
COPY package.json package-lock.json ./

# Install dependencies with npm install
RUN npm install

# Copy all the application files
COPY . .

# Create a directory for the SQLite database file with the command
RUN mkdir -p /app/data

# Expose port 5000 (the port your backend runs on)
EXPOSE 5000

# Start the application with npm start
CMD ["npm", "start"]
