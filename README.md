# rpi-plex-samba
Raspberry Pi with Plex server and Samba local network disc sharing.

## Plex config
* https://hub.docker.com/r/linuxserver/plex
```yml
    volumes:
      - /path/to/library:/config
      - /path/to/tvseries:/tv
      - /path/to/movies:/movies
```
## Samba config
* https://hub.docker.com/r/dperson/samba
* https://github.com/dperson/samba
* https://github.com/dperson/samba/blob/master/docker-compose.yml