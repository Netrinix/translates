![](https://blog.xpdbk.com/post/mc-server/game_hu9a1df71d11008168eefdfe4a7f4c554c_45444_1600x0_resize_q75_h2_box_2.webp)

# use VPS Made the Minecraft Server (Linux)
1. why?
when we play Minecraft, maybe we need multiplayer. but in Minecraft: Java Edition only LAN online. then we need made a server, to allow different players who are not in the LAN to be online.


2. install environment
VPS system：Ubuntu 22.04 64位
Minecraft version：Minecraft : Java Edition 1.12.2
3. Steps

1. Install the JDK 8. [Click this](https://www.oracle.com/cn/java/technologies/downloads/)

If you don't know how to install(or your server only can ssh), you can use baidu, google or bing to search how to use ssh install jdk8.

1.16- version use jdk8

## Use SSH Install JDK (version 1.16-)
`sudo apt install openjdk-8-jdk`

## Use SSH Install JDK (1.17+)
`sudo apt install openjdk-16-jdk`

## Use SSH Install JDK (1.18+)
`sudo apt install openjdk-17-jdk`

# Server Main Jar Download
Click [This](https://mcversions.net/), find your server version.

copy the server.jar download URL(Right click hyperlink and click the "copy download url")

![](https://blog.xpdbk.com/post/mc-server/666.webp)

## Use SSH Download Server
`wget -N {URL}`
{URL} replace to you copied URL.

# Use Command Terminal Open Server
`java -server -XX:+UseG1GC  -Xmx2048M -Xms1024M -jar server.jar nogui`
Open `eula.txt`, edit `eula=false` to `eula=true`

![](https://blog.xpdbk.com/post/mc-server/awda_hu4dc607e55e7c9e68bb96435168389937_19942_1024x0_resize_q75_h2_box_2.webp)

Open `server.properties` file, edit this:
```properties
view-distance=10
max-build-height=256
server-ip=
level-seed=
gamemode=0 # Default Gamemode. 0: Survival 1: Creative 2: Spectator
server-port=25565 # Server Port, if this is `20002`, server ip maybe is this: ip:20002
enable-command-block=false 
allow-nether=true
enable-rcon=false
op-permission-level=4
enable-query=false
generator-settings=
resource-pack=
player-idle-timeout=0
level-name=world
motd=A Minecraft Server # Under the Server Name
announce-player-achievements=true
force-gamemode=false
hardcore=false
white-list=false
pvp=true
spawn-npcs=true
generate-structures=true
spawn-animals=true
snooper-enabled=true
difficulty=1
network-compression-threshold=256
level-type=DEFAULT
spawn-monsters=true
max-tick-time=60000
max-players=20 # Max player. if bigger, server kick a player description is 'Server full'.
use-native-transport=true
online-mode=true # if you support offline mode, please edit this to false.
allow-flight=false
resource-pack-hash=
max-world-size=29999984
```

Create a Start Shell.
Create a file: start.sh and write this:
```sh
for ((i=0; i<10; i ++))
do
	java -server -XX:+UseG1GC  -Xms1024M -Xmx2048M -jar server.jar nogui -noverify -XX:+AggressiveOpts -XX:+UseCompressedOops
done
```
and save.


# Give permission
```
chmod 777 start.sh
```
Run this to Give perm.
> ***Attention***
Stop Server please run server command stop.


# Server launch done
![](https://blog.xpdbk.com/post/mc-server/dfwerf_huff4d15e65c72e7b93d5a19f7e1e13d06_60768_1024x0_resize_q75_h2_box_2.webp)
