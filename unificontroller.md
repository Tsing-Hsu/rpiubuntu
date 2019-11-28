# Unifi Controller 

## source
[https://help.ubnt.com/hc/en-us/articles/220066768-UniFi-How-to-Install-and-Update-via-APT-on-Debian-or-Ubuntu]

[https://community.ui.com/questions/UniFi-Installation-Scripts-or-UniFi-Easy-Update-Script-or-UniFi-Lets-Encrypt-or-Ubuntu-16-04-18-04-/ccbc7530-dd61-40a7-82ec-22b17f027776]

## install 

```
sudo apt update && sudo apt install ca-certificates apt-transport-https
```

```
echo 'deb https://www.ui.com/downloads/unifi/debian stable ubiquiti' | sudo tee /etc/apt/sources.list.d/100-ubnt-unifi.list
```

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 06E85760C0A52C50 
```

```
sudo apt update && sudo apt install unifi
```

## access

`serverip:8443`
