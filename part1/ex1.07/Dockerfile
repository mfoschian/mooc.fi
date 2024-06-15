FROM ubuntu:22.04

WORKDIR /usr/src/ex1.07


RUN apt-get update
RUN apt-get install -y curl

COPY script.sh .

RUN chmod a+x script.sh


CMD ./script.sh
