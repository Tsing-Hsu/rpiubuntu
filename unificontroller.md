# Unifi Controller on Raspberry Pi 3

## Requirements

* raspberry pi 3
* 4GB or greater micro SD-card

## unifi controller on raspbian

Download Raspbian Buster Lite from https://www.raspberrypi.org/downloads/raspbian/ .

Flash on micro SD-card,

Create empty file named `ssh` on boot partition.

Boot from sdcard.

Find out IP-address x.x.x.x .

ssh into rpi with user pi passord raspberry

```
ssh pi@x.x.x.x
```

change password

```
passwd
```

```
sudo apt update
sudo apt upgrade -y

sudo apt install haveged -y
sudo raspi-config
```

Change under Advanced Options, Memory Split to 16
Expand File system
change timezone and locale

reboot

```
sudo reboot
sudo apt install apt-transport-https
```

add keys for unifi

```
sudo wget -O /etc/apt/trusted.gpg.d/unifi-repo.gpg https://dl.ui.com/unifi/unifi-repo.gpg 
```

add sources for unifi
```
echo 'deb https://www.ui.com/downloads/unifi/debian stable ubiquiti' | sudo tee /etc/apt/sources.list.d/100-ubnt-unifi.list
```

```
sudo apt update
sudo apt install unifi
```

## advanced unifi configuration

Create `/usr/lib/unifi/sites/default`

```
cd /usr/lib/unifi/data
sudo mkdir ./sites
sudo mkdir ./sites/default
sudo chown -R unifi:unifi ./sites
sudo chmod -R u=rwx,g=rx,o= sites
```

Create `config.gateway.json` in `/usr/lib/unifi/data/sites/default

```
cd /usr/lib/unifi/data/sites/default
sudo nano config.gateway.json
```

verify json syntax

```
python -m json.tool config.gateway.json
```

Change ownership 
```
chown unifi:unifi config.gateway.json
```

## 
Download Ubuntu 18.04.x 32-bit from here: [https://ubuntu.com/download/raspberry-pi]

Find out IP adress.

ssh into rpi
``` 
ssh ubuntu@x.x.x.x
```
where x.x.x.x is ip address of rpi

change password, relogin

```
sudo apt update
sudo apt upgrade -y
sudo apt install apt-transport-https
sudo reboot
```

relogin using ssh

add keys for unifi
```
sudo wget -O /etc/apt/trusted.gpg.d/unifi-repo.gpg https://dl.ui.com/unifi/unifi-repo.gpg 
```

add sources for unifi

```
echo 'deb https://www.ui.com/downloads/unifi/debian stable ubiquiti' | sudo tee /etc/apt/sources.list.d/100-ubnt-unifi.list
```

install mongodb database keys and sources
```
wget -qO - https://www.mongodb.org/static/pgp/server-3.4.asc | sudo apt-key add -
echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
sudo apt update
```

## source
[https://help.ubnt.com/hc/en-us/articles/220066768-UniFi-How-to-Install-and-Update-via-APT-on-Debian-or-Ubuntu]

[https://community.ui.com/questions/UniFi-Installation-Scripts-or-UniFi-Easy-Update-Script-or-UniFi-Lets-Encrypt-or-Ubuntu-16-04-18-04-/ccbc7530-dd61-40a7-82ec-22b17f027776]

## install 

```
sudo apt update && sudo apt install ca-certificates apt-transport-https
```

### install via apt does not work yet
```
echo 'deb https://www.ui.com/downloads/unifi/debian stable ubiquiti' | sudo tee /etc/apt/sources.list.d/100-ubnt-unifi.list
```

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 06E85760C0A52C50 
```

```
sudo apt update && sudo apt install unifi
```


### manual install

```
wget https://get.glennr.nl/unifi/install/install_latest/unifi-latest.sh; 
chmod +x unifi-latest.sh; 
sudo ./unifi-latest.sh
```


## access

`serverip:8443`
