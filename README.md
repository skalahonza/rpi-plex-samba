# rpi-plex-samba
Raspberry Pi with Plex server and Samba local network disc sharing.

# Installation
## 1. Setup
* (Optional) install NTFS compatibility tool `sudo apt-get install ntfs-3g -y`
* Install Docker and Docker Compose
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ${USER}
sudo su - ${USER}
sudo apt-get install libffi-dev libssl-dev
sudo apt install python3-dev
sudo apt-get install -y python3 python3-pip
sudo pip3 install docker-compose
```
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
/dev/sda1       /mnt            ntfs    nofail          0       0
```

## 3. Launch
* Go to https://plex.tv/claim
* Copy your code
* Set your code as variable `export TOKEN="yourtoken"`
* In **/mnt** folder run `docker-compose up -d`
* Go to https://app.plex.tv/desktop
* Setup your Plex server
* Put all your movies into **plex/movies** folder
* Put all your tv series in **plex/tv folder**

# Notes
## Plex source image
* https://hub.docker.com/r/linuxserver/plex
```yml
    volumes:
      - /path/to/library:/config
      - /path/to/tvseries:/tv
      - /path/to/movies:/movies
```
## Samba source image
* https://hub.docker.com/r/dperson/samba
* https://github.com/dperson/samba
* https://github.com/dperson/samba/blob/master/docker-compose.yml
