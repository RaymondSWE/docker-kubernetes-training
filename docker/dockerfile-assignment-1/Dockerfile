FROM node:6-alpine

# Expose port 3000
EXPOSE 3000
# run alpine package manager to install tini
RUN apk add --no-cache tini

# Create app directory with workdir
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json package.json

# Install app dependencies use command chaining to reduce image size (&&)
RUN npm install && npm cache clean --force

# Copy app source code (make sure its space between . .)
COPY . .

# Run app look at docker file builder reference for more info
CMD ["tini", "--", "node", "./bin/www"]


## Build the image, just give it random name as most likely you will not use it or fail building first time
# docker build -t testnode .
## use -rm to remove intermediate containers after a successful build
# docker container run --rm -p 80:3000 testnode 
