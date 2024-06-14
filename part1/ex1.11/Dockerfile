FROM amazoncorretto:8

WORKDIR /usr/src/ex1.11

COPY spring-example-project .

# Make sure that maven script is executable
RUN chmod a+x mvnw

# start proxy configuration block {
# comment if you are not behind a proxy

ARG PROXY_HOST=my.proxy.it
ARG PROXY_PORT=3128
ARG PROXY_URL=http://${PROXY_HOST}:${PROXY_PORT}
ARG HTTPS_PROXY_URL=http://${PROXY_HOST}:${PROXY_PORT}

# proxy configuration for maven-wrapper
RUN mkdir -p .mvn
RUN echo -Dhttp.proxyHost=${PROXY_HOST} >> .mvn/jvm.config
RUN echo -Dhttp.proxyPort=${PROXY_PORT} >> .mvn/jvm.config
RUN echo -Dhttps.proxyHost=${PROXY_HOST} >> .mvn/jvm.config
RUN echo -Dhttps.proxyPort=${PROXY_PORT} >> .mvn/jvm.config

# proxy configuration for curl
ENV http_proxy=${PROXY_URL}
ENV https_proxy=${HTTPS_PROXY_URL}
#
# end proxy configuration block }


RUN ./mvnw package

EXPOSE 8080

CMD ["java", "-jar", "./target/docker-example-1.1.3.jar"]
