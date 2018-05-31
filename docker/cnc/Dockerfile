FROM ubuntu:latest

# Install requirements + utilities
RUN apt-get update \
 && apt-get install --yes dnsutils iputils-ping openssh-server nano

COPY ./cnc /opt/cnc

WORKDIR /opt

#Run instruction
#docker run --name miraicnc --network dockernet --ip 192.0.0.225 -i -d -t mirai-bc:cnc
