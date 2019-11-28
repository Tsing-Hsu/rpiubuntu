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

## install MicroK8s

### enable cgroup


in /boot/cmdline.txt

```
cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1
```
