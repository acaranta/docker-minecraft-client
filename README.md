# Docker container for Minecraft Client

This is a Docker container for [Minecraft Java Client](https://www.minecraft.net).
This is a proof of concept ^^

The GUI of the application is accessed through a modern web browser (no installation or configuration needed on client side) or via any VNC client.

---

# How to run it
## First build the container
```
git clone https://github.com/acaranta/docker-minecraft-client.git
cd docker-minecraft-client
docker build -t mcclient .
```

## Then Run it
```
docker run -d --name mcclient -p 5800:5800 -p 5900:5900 -v <LOCALPATHDIR>:/config/.minecraft mcclient
```
## Or just run it
Or, if you don't want to build it, this repository get build after each commit into docker hub : https://hub.docker.com/r/acaranta/docker-minecraft-client
```
docker run -d --name mcclient -p 5800:5800 -p 5900:5900 -v <LOCALPATHDIR>:/config/.minecraft acaranta/docker-minecraft-client
```
where :
* LOCALPATHDIR is the local directory where minceracft launcher/login data will be saved between sessions
* 5800-5900 ports are VNC ports

## Access it
just use your regular web browser to reach : 
`http://<YOURDOCKERHOST>:5800`
and voila !

### Gameplay
NB : For mouse to work "properly", in Minecraft :
* Go to : `Options->Controls->Mouse Settings`
* Make sure `Raw input` is OFF
* Decrease Sensitivity to 50% (and adjust to your liking :) )

# SECURITY NOTICE
This is indeed a proof of concept and overall it should not used (if useable anyway lol) because :
* this is http only, traffic is nt encrypted
* there is no password to accss the vnc display
* Files will be stored on your machine, but you are responsible for securing the local storage
