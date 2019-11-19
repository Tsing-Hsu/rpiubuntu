# for ubuntu server 64bit 19.10


## install wireguard
```
sudo add-apt-repository ppa:wireguard/wireguard
```

```
sudo apt install wireguard
```

## generate keys 
```
(umask 077 && printf "[Interface]\nPrivateKey = " | sudo tee /etc/wireguard/wg0.conf > /dev/null)
wg genkey | sudo tee -a /etc/wireguard/wg0.conf | wg pubkey | sudo tee /etc/wireguard/publickey
```

## generate config file
```
sudo nano /etc/wireguard/wg0.conf

[Interface]
PrivateKey = YOUR_SERVER_PRIVATE_KEY
ListenPort = 51280
SaveConfig = false
Address = 10.0.0.1/24
```
##
