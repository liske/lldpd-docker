# lldpd - LLDP daemon (IEEE 802.1AB) 

This is a docker image for [lldpd](https://vincentbernat.github.io/lldpd/) based on the offical Debian packages.


## Tagged Docker Images

Images are tagged according to the installed lldpd version. All images are build using different Debain GNU/Linux releases.

* [`0.9.6`, `latest` Dockerfile](https://github.com/DE-IBH/lldpd-docker/blob/master/lldpd-0.9.6-debian/Dockerfile)

  [![Layers](https://images.microbadger.com/badges/image/ibhde/lldpd:0.9.6.svg)](https://images.microbadger.com/badges/image/ibhde/lldpd:0.9.6)
  This image is build using *Debian stretch* and should be considered **stable** (*recommended*).


* [`0.7.11` Dockerfile](https://github.com/DE-IBH/lldpd-docker/blob/master/lldpd-0.7.11-debian/Dockerfile)

  [![Layers](https://images.microbadger.com/badges/image/ibhde/lldpd:0.7.11.svg)](https://images.microbadger.com/badges/image/ibhde/lldpd:0.7.11)
  This image is build using *Debian jessie* and should be considered **obsolete**.


## Usage

```
$ docker run --rm --net=host --uts=host --cap-add=NET_ADMIN --cap-add=NET_RAW ibhde/lldpd
```

The command is used as options for lldpd (which is already the entrypoint). By default the option `-k` is used.
Feel free to change the behavior by passing [lldpd options](https://vincentbernat.github.io/lldpd/usage.html#lldpd8)
as command.

```
# docker-compose.yml example
version: '3'
services:
  lldpd:
    image: ibhde/lldpd
    cap_add:
      - NET_ADMIN
      - NET_RAW
    network_mode: host
    hostname: myhostname
    # LLDPD options: hide kernel details and enable CDP
    command: ["-k", "-c"]
```
