# Use the official lightweight Node.js 16 image.
# https://hub.docker.com/_/node
FROM node:16-slim

# Create and change to the app directory.
WORKDIR /usr/src/app

# Copy application dependency manifests to the container image.
# A wildcard is used to ensure both package.json AND package-lock.json are copied.
COPY package*.json ./

# Install production dependencies.
RUN npm install --only=production

# Copy local code to the container image.
COPY . .

# Build the React application.
RUN npm run build

# Install serve to run the application.
RUN npm install -g serve

# Serve the production build on container startup.
CMD ["serve", "-s", "build", "-l", "3000"]

# Expose the port the app runs on.
EXPOSE 3000
