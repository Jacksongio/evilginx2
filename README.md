# Evilginx 3.0 install notes - Jackson Giordano
Most notes from this are derived from this youtube video: https://www.youtube.com/watch?v=r4Y53s6P51k

And alot of notes from this website, although it could be blocked from certain networks due to its security so I would not access it personally.
    https://evilginx.com/ 


## Setting up server
 1. Through Azure setup an Ubuntu server
 - Ubuntu Version 22.04 region America.
 - setup ssh into PuTTY from computer
 2. Setup up Domain name
 - Not too sure how we could do this, unless we have access to Microsofts Web hosting functionality
## Open Terminal and log into server

    ssh root@[ENTERIPADDRESSHERE]

    apt update
 
    apt upgrade

    apt install golang

    git clone https://github.com/kgretzky/evilginx2
    
    cd evilginx2

    go build

    ./evilginx2
    
    exit
## Adding Config

    cd root/.evilginx2

    nano config.json

- replace domain with our domain for phishing
- replace external ipv4 with the IP from azure ubuntu server


## Create Phishlet

    cp phishlets/example.yaml phislets/ASTest.yaml

- I updated ASTest.yaml for our specific testing purposes
- We still need to replace the two sections with our test domain

## Deploy Phishlet

    phishlets hostname AStest EXAMPLEDOMAIN
    
    phishlets enable AStest

## Retrieve Lure

    lures get-url 0
# That should be it!!!
