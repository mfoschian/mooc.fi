FROM golang:1.16

WORKDIR /usr/src/backend

# sources from https://github.com/docker-hy/material-applications/ cloned in upper folders
COPY example-backend .

# proxy section: comment if not behind a proxy {
# ARG PROXY_URL=http://my.proxy.it:3128
# ARG HTTPS_PROXY_URL=https://my.proxy.it:3129
# ENV http_proxy=${PROXY_URL}
# ENV https_proxy=${HTTPS_PROXY_URL}
# end of proxy section }


# Build server binary
ARG cors=http://localhost:5000
ARG redis_host=
ENV PORT=8080
ENV REQUEST_ORIGIN=$cors
ENV REDIS_HOST=$redis_host
RUN go build

# Run tests
RUN go test ./...

# Expose container port 8080
EXPOSE $PORT

# By default start serve listening on port 5000 and serving build subfolder
CMD ["./server"]


