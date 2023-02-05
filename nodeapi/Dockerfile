# Build the nodeapi image in seperate image
FROM node:14 AS nodeapi_build
WORKDIR /usr/src/app
COPY ./ ./nodeapi/

# npm install will download all dependecies which is required
RUN cd nodeapi && npm install

# Copy the output to new node image to run 
FROM node:14
WORKDIR /usr/src/app
COPY --from=nodeapi_build /usr/src/app/nodeapi/ ./

# Expose port allow to listen traffic on specific port 
EXPOSE 5000

# Start the Node Service
CMD ["/bin/sh", "-c", "cd /usr/src/app/ && npm start"]