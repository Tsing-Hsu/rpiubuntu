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

```

