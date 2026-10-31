# Use a Node.js base image for the build stage
FROM node:18-alpine

# Set a working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json files
COPY package.json package-lock.json ./

# Install dependencies with npm install
RUN npm install

# Accept build argument 
ARG VITE_API_URL 
ENV VITE_API_URL=$VITE_API_URL

# Copy all the application files
COPY . .

# Build the production application with npm run build
RUN npm run build

# Use nginx to serve the built files (multi-stage build)
FROM nginx:alpine
COPY --from=0 /app/dist /usr/share/nginx/html

# Expose port 80 (nginx default port)
EXPOSE 80

# Start nginx to serve the application
CMD ["nginx", "-g", "daemon off;"]
