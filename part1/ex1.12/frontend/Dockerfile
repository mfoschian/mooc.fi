# Exercise seems to need v16 
FROM node:16.20.0

WORKDIR /usr/src/frontend

# sources from https://github.com/docker-hy/material-applications/tree/main/example-frontend saved in "example-frontend" local folder
# copy git sources to image
COPY example-frontend ./

# Comment if you are not behind a proxy
# RUN npm config set proxy http://my.proxy.it:3128
# RUN npm config set https-proxy https://my.proxy.it:3128

# Build a layer with serve tool pre-installed
RUN npm install -g serve

# Install node modules (this take a while for package-lock.json coming from older npm ...)
RUN npm install

# needed for node versions >= 17
# RUN export NODE_OPTIONS=--openssl-legacy-provider

# Build frontend
RUN npm run build

# Expose container port 5000
EXPOSE 5000

# By default start serve listening on port 5000 and serving build subfolder
CMD ["serve", "-s", "-l", "5000" ,"build"]


