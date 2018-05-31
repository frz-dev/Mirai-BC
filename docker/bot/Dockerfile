FROM ubuntu:latest

# Install requirements + utilities
RUN apt-get update \
 && apt-get install --yes dnsutils iputils-ping telnet openssh-client

COPY ./mirai /opt/mirai

WORKDIR /opt

#Man
#docker build -t mirai-bc:bot .
#docker run --name miraibot --network dockernet --dns=192.0.0.100 -it mirai-bc:bot
