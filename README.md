# Appi CLI Documentation

<img src="logo.png" width="400">


![build succeeded](https://img.shields.io/badge/build-succeeded-brightgreen.svg) ![Test passing](https://img.shields.io/badge/Tests-passing-brightgreen.svg)

## About Appi, TL;DR


Appi is a Low Code / No Code framework build on an distributed data pipeline. Out of the box Appi aims to provides everything you need to release, operate and maintain services, backends and fullstack applications.


## About Appi-CLI


Appi-CLI provides a command line inerface into the Appi Ecosystem. It is used to run Appi Server Instances, Backend Services and Edge Clients.

Appi comes in two versions: Community Edition, which it a freely available public version; And Enterprise Edition, which is a paid commercial product. The primary distinction is that the community edition is limited to a single node, where the enterprise edition supports clustering and sharding.


### Community Server

1. Create Server Container:

    A. Volatile: `docker run -d -t -p 8099:8099 --hostname appi --name appi agardnerut/appi-cli`

    B. Persistant with Volumes: `docker run  -p 8099:8099 -v c:/Appi/fs:/root/appifs -v c:/Appi/history:/root/appihistory -v c:/Appi/static:/root/staticfs --hostname appi --name appi -d -t agardnerut/appi-cli`

2. Run Appi Server:

    A. With Tests: `docker exec appi ./appi-cli --serve --test --logging 1 --sudo TESTSECRET`

3. Things you might want to do: 

    A. Check what is Running: `docker top appi`

    B. Manage the container: `docker attach appi`


### Service


1. Create Service Container: 

    A.`docker run -d -t --hostname service --name service agardnerut/appi-cli`

    B. Persistant with Volumes: `docker run -d -t -v c:/AppiService/fs:/root/appifs -v c:/AppiService/history:/root/appihistory -v c:/AppiService/static:/root/staticfs --hostname service --name service agardnerut/appi-cli`

2. Run Service Commands: 

    A. `docker exec appi ./appi-cli --addr 0 --tail SYSTEM --host appi:8099 --sudo TESTSECRET`

    B. `...`