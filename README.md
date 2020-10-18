# rpi-plex-samba
Raspberry Pi with Plex server and Samba local network disc sharing.

## Plex config
```yml
    volumes:
      - /path/to/library:/config
      - /path/to/tvseries:/tv
      - /path/to/movies:/movies
```
## Samba config