[![Docker Pulls](https://img.shields.io/docker/pulls/jimmysong76/armory-vnc.svg)](https://hub.docker.com/r/jimmysong76/armory-vnc/)
[![Docker Stars](https://img.shields.io/docker/stars/jimmysong76/armory-vnc.svg)](https://hub.docker.com/r/jimmysong76/armory-vnc/)

armory-vnc
===
Simple VNC-connectable docker container that uses:

 * Ubuntu Core 14.04
 * LXDE desktop
 * TightVNC server
 * Bitcoin 0.12.1
 * Armory 0.94.1

*YOU SHOULD STILL SIGN ON AN OFFLINE MACHINE, USE THIS ONLY FOR YOUR WATCH-ONLY WALLET!!*

Build
-----
Include password.txt with the password for TightVNC (by default this is "password"). This must be at least 8 characters and is truncated if longer.

Usage
-----
You can build with

    (host) $ docker build -t armory-vnc .

Create and start with

    (host) $ id
    uid=XXXX(YYYY) gid=ZZZZ(YYYY)
    (host) $ docker create --name=armory -p 5901:5901 -v <bitcoin dir>:/bitcoin -v <armory dir>:/armory -e PUID=XXXX -e PGID=ZZZZ armory-vnc
    (host) $ docker start armory

You can connect to the vnc server using at SERVER_NAME:5901 using the password from password.txt (default is "password") where SERVER_NAME is the docker container host's name or IP.

Within the container, you can start up armory as normal.

    (container) $ armory


Credit
------

Based off of the docker image [kaixhin/vnc](https://github.com/Kaixhin/dockerfiles/tree/master/vnc).