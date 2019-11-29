# Ubuntu Server 19.10 64-bit on RPI 3

##

##

default login is user `ubuntu`, password `ubuntu`

customize user in 'user-data' file on the 'system-boot' partition

1st login, change password

login again

```
sudo apt update
sudo apt upgrade -y
```

### enable cgroup


in `/boot/firmware/nobtcmd.txt`
apppend
```
cgroup_enable=memory cgroup_memory=1
```

reboot with

```
sudo reboot
```

check

```
cat /proc/cmdline
```

```
cat /proc/cgroups
```

### install docker

```
sudo snap install docker
```

### install traefik

```
docker run -d -p 8080:8080 -p 80:80 -v $PWD/traefik.toml:/etc/traefik/traefik.toml traefik
```
