## get a dyn dns provider

In our case, we use spDYN from <www.spdyn.de>

Create host <host_name>

Create Update-Token <update_token>

## setup ddclient

```
sudo apt install ddclient
```

```
sudo nano /etc/ddclient.conf
```

use server: update.spdyn.de

use protocol: dyndns2

username: <host_name>
password: <update_token>
