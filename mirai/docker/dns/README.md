# BIND-dock
Generic BIND server docker container. - Private Network Setup

This container is meant for testing purposes and it is supposed to be configured as needed.

Default config answers requests for www.domain.com with the IP 1.2.3.4

## Set-up
```sh
docker network create --internal --subnet 192.0.0.0/24 dockernet
docker build -t binddock:private .
docker run --name binddock --network --ip 192.0.0.100 -i -d -t binddock:private
```

## Test
To test the DNS server:
```sh
$ BINDsrv=$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' binddock)
$ nslookup - $BINDsrv
> www.domain.com
Server:		172.17.0.2
Address:	172.17.0.2#53

Name:	www.domain.com
Address: 1.2.3.4
>
```

* Using the test container:
```sh
$ cd test
$ docker build -t nettest .
$ docker run --network dockernet --dns=192.0.0.100 -it nettest
# nslookup
> www.domain.com
Server:		127.0.0.11
Address:	127.0.0.11#53

Name:	www.domain.com
Address: 1.2.3.4
> 
```

## MAN
* Enter the container shell:
```sh
$ docker attach binddock
root@a1eba089c6e5:~#
```

* Exit the container (without killing the process):<br/>
Press `'Ctrl+p`, followed by `Ctrl+q`

* Terminate the container:
```sh
$ docker kill binddock
```
* Restart the container:
```sh
$ docker start binddock
```

* Remove the container:
```sh
$ docker kill binddock
```
