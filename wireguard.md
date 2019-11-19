# for ubuntu server 64bit 19.10


## install wireguard
```
sudo add-apt-repository ppa:wireguard/wireguard
```
https://medium.com/@aveek/setting-up-pihole-wireguard-vpn-server-and-client-ubuntu-server-fc88f3f38a0a

```
sudo apt install wireguard
```

## generate keys 
```
(umask 077 && printf "[Interface]\nPrivateKey = " | sudo tee /etc/wireguard/wg0.conf > /dev/null)
wg genkey | sudo tee -a /etc/wireguard/wg0.conf | wg pubkey | sudo tee /etc/wireguard/publickey
```

## setup on android

Download Wireguard.

click + sign, select create from scratch.

Name: yourname

Private key, click generate
Puplic key, copy 

adresses: 10.0.0.2/32

DNS servers: 8.8.8.8

add peer
Puplic key YOUR_SERVER_PUBLIC_KEY
allowed IP 0.0.0.0/0

endpoint: 
router address /pi address: port


## modify config file
```
sudo nano /etc/wireguard/wg0.conf

[Interface]
PrivateKey = YOUR_SERVER_PRIVATE_KEY
ListenPort = 51280
SaveConfig = false
Address = 10.0.0.1/24
PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

[Peer]
PublicKey = PUBLIC_KEY_ON_ANDROID
AllowedIPs = 10.0.0.2/32
```

## check if working

```
sudo wg-quick up wg0
sudo wg
sudo wg-quick down wg0
```

## wireguard as service

```
sudo systemctl enable wg-quick@wg0
```

## enable forwarding

```
sudo nano /etc/sysctl.conf
```

uncomment following lines

```
net.ipv4.ip_forward = 1
```

and 

```
net.ipv6.conf.all.forwarding = 1
```

```
sudo sysctl -p
```
