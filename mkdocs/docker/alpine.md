# Linux Alpine

```bash
docker run --rm -ti -v $(pwd):/app -w /app alpine:latest sh
```

## How to install redis-cli and psql client on your machine with Docker Alpine 

### Preparing docker images
We will use minimalistic Linux distribution called Alpine (5MB)

#### Dockerfile of redis-cli
```
FROM alpine:latest
RUN apk --update add redis

ENTRYPOINT ["redis-cli"]
```
#### Creating redis-cli docker image (~7MB)
```sh
docker build -t redis-cli .
```

#### Dockerfile of psql client
```
FROM alpine:latest
RUN apk --update add postgresql-client

ENTRYPOINT ["psql"]
```
#### Creating psql docker image (~7MB)
```sh
docker build -t psql .
```

## Add aliases into our ~/.bash_profile
Place these lines into your .bash_profile
```sh
alias psql='docker run --rm -it psql'
alias redis-cli='docker run --rm -it redis-cli'
```

## Restart your terminal and that's it
You can test it by running this:
```sh
redis-cli --help
psql --help
```
Bear in mind that dotfiles (rc files) will not work with this configuration.

------

## Install telnet into alpine image

```
>>> docker exec -it CONTAINERID /bin/sh
/app # telnet
/bin/sh: telnet: not found

/app # apk update
fetch http://dl-cdn.alpinelinux.org/alpine/v3.7/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.7/community/x86_64/APKINDEX.tar.gz
v3.7.0-243-gf26e75a186 [http://dl-cdn.alpinelinux.org/alpine/v3.7/main]
v3.7.0-229-g087f28e29d [http://dl-cdn.alpinelinux.org/alpine/v3.7/community]
OK: 9051 distinct packages available

/app # apk add busybox-extras
(1/1) Installing busybox-extras (1.27.2-r11)
Executing busybox-extras-1.27.2-r11.post-install
Executing busybox-1.27.2-r7.trigger
OK: 77 MiB in 64 packages

/app # busybox-extras telnet localhost 6900
```

## Install mongo client into alpine image

```
echo 'http://dl-cdn.alpinelinux.org/alpine/v3.9/main' >> /etc/apk/repositories
echo 'http://dl-cdn.alpinelinux.org/alpine/v3.9/community' >> /etc/apk/repositories
apk update
apk add mongodb yaml-cpp=0.6.2-r2
mongo -version
```

## Install mysql client into alpine image

```
apk update 
apk add mysql mysql-client 
mysql --version
```