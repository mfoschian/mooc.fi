FROM node

WORKDIR /srv/www/faceTracker

# run build with --build-arg="sproxy=https://yourproxy.com:port" if behinde a proxy server
ARG proxy=
ARG sproxy=

# Clone the github repository
RUN <<EOF
if [ -n $sproxy ]; then
	echo "Using https_proxy: $sproxy"
	export https_proxy=${sproxy}
	npm config set https-proxy ${sproxy}
fi
if [ -n $proxy ]; then
	echo "Using http_proxy: $proxy"
	export http_proxy=${proxy}
	npm config set proxy ${proxy}
fi
git clone https://github.com/mfoschian/faceTracker.git .
EOF

RUN npm install -g serve 

RUN npm install
RUN npm run build

EXPOSE 80

# By default start serve listening on port 5000 and serving build subfolder
CMD ["serve", "-s", "-l", "80" ,"dist"]
