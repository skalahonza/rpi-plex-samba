# rpi-plex-samba
Raspberry Pi with Plex server and Samba local network disc sharing.

# Installation
## 1. Setup
* Download this repo
* Copy on the root folder of your hard drive
* Plug into your RPI

## 2. Mount external hard drive
### Mount external hard drive
`sudo mount /dev/sda1 /mnt`

### Modify fstab for auto mounting
`sudo nano /etc/fstab`

Add:
**/dev/sda1       /mnt            ntfs    defaults          0       0**

then it should look like this

```
proc            /proc           proc    defaults          0       0
/dev/mmcblk0p6  /boot           vfat    defaults          0       2
/dev/mmcblk0p7  /               ext4    defaults,noatime  0       1
/dev/sda1       /mnt            ntfs    defaults          0       0
```

## 3. Launch
* Go to https://plex.tv/claim
* Copy your code
* In **/mnt** folder run `docker-compose up -e TOKEN=yourtoken -d`
* Go to https://app.plex.tv/desktop
* Setup your Plex s

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