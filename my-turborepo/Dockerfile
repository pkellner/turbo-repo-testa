# Use the official Node.js image based on Alpine
FROM node:18-alpine

# Set the working directory
WORKDIR /app

# Copy project files into the container
COPY . .

# Install dependencies
RUN npm install

# Expose the port the app runs on
EXPOSE 3000

# Start an interactive shell
WORKDIR /app/apps/web

CMD ["npm", "start"]
