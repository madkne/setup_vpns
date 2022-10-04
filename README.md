# OpenVPN Setup

## install Openvpn server on debian/ubuntu servers

1. download openvpn installer with `curl -O https://raw.githubusercontent.com/angristan/openvpn-install/master/openvpn-install.sh`
2. run installer with some specific parameters:
    - tcp protocol
    - DNS 1.1.1.1

3. create first openvpn client
4. then set final .ovpn file to a openvpn client


## connect to openvpn client

> every ovpn client can used for one device (connection)

### via terminal (linux, mac)
```
sudo openvpn --config ~/Desktop/madkne.ovpn
```
### android app

download from `https://github.com/schwabe/ics-openvpn/releases/tag/v0.7.41`

### windows app

download from `https://openvpn.net/client-connect-vpn-for-windows/`


## install openvpn admin panel

1. install docker on server
2. install old version of docker compose with:
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

```
2. clone from repo `git clone https://github.com/flant/ovpn-admin`
3. `cd ovpn-admin`
4. run `./start.sh`