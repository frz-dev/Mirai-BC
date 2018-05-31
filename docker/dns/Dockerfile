# BIND DNS Server docker image

FROM ubuntu:latest

# Install requirements + utilities
RUN apt-get update \
 && apt-get install --yes bind9 bind9utils rsyslog tcpdump dnsutils

RUN mkdir /var/log/named \
&& chown -R bind:root /var/log/named \
&& chmod -R 775 /var/log/named

# Set up BIND9
COPY ./bind/* /etc/bind/
COPY ./bind/zones /etc/bind/zones
RUN echo "alias dnslog='tcpdump -i eth0 -vvv -s 0 -l -n port 53 &'" >> ~/.bashrc

WORKDIR /root/

EXPOSE 53/udp 53/tcp

ENTRYPOINT /etc/init.d/bind9 start \
  && echo "nameserver 127.0.0.1" > /etc/resolv.conf \
  && /bin/bash
