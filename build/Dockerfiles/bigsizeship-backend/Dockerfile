FROM node:18
# Set the working directory and copy the necessary files
WORKDIR /opt/
COPY package*.json ./
RUN npm config set fetch-retry-maxtimeout 600000 -g && npm install 
ENV PATH /opt/node_modules/.bin:$PATH

# Set the working directory for the app
WORKDIR /opt/app
COPY . .
RUN chown -R node:node /opt/app

# Switch to the 'node' user to avoid running as root
USER node

# Build the app
RUN ["npm", "run", "build"]

# Expose the required port
EXPOSE 1337

# Start the app in development mode
CMD ["npm", "start"]
