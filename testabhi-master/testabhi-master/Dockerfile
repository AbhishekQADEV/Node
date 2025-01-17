FROM node:21-alpine

# Set working directory
WORKDIR /usr/src/app

# Copy all files from current directory to working directory
COPY . .

# Install dependencies
RUN npm install

# Expose port 80
EXPOSE 80

# Start the application
CMD [ "npm", "start" ]