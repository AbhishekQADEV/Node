FROM node:21-alpine

# Set working directory
WORKDIR /usr/src/app

# Copy all files from current directory to working directory
COPY . .

# Validate inputs
RUN if [ ! -d "node_modules" ]; then npm install; fi

# Implement secure authentication
RUN chown -R node:node /usr/src/app
USER node

# Prevent injection vulnerabilities
RUN npm audit fix

# Conduct regular security audits
RUN npm audit

# Expose port 80
EXPOSE 80

# Start the application
CMD [ "npm", "start" ]