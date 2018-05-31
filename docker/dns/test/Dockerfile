# Network test docker image

FROM ubuntu:latest

# Install requirements + utilities
RUN apt-get update \
 && apt-get install --yes dnsutils tcpdump

# Set up BIND9
RUN echo "alias dnslog='tcpdump -i eth0 -vvv -s 0 -l -n port 53 &'" >> ~/.bashrc

WORKDIR /root/

EXPOSE 53/udp 53/tcp

ENTRYPOINT /bin/bash
