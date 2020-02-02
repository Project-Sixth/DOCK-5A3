# General information
Docker for Forge Minecraft Server, based on Debian Stretch (`debian:9`).
Sadly, couldn't fit that to `debian:9-slim` for some reason.
## Fast start
  1. `docker run --name minecraftspigot-server --volume /srv/minecraft-spigot:/data --publish 25565:25565 --restart unless-stopped --detach theprojectsix/minecraftspigot-server:1.14.4`
   - *this will download all server files and run server once*
  2. `docker stop minecraftspigot-server`
  3. Configure as needed (manually)
  4. `docker start minecraftspigot-server`
 
# Build/Run information
### Build Arguments
  - PUID = 1000 *- user ID that will run server*
  - PGID = 1000 *- group ID that will run server*
  - MINECRAFT_VERSION = 1.12.2 *- needed minecraft version
  - BUILDTOOLS_VERSION = lastSuccessfulBuild *- needed buildtools version

### Enviromental Variables
  - MIN_RAM = 1G *- minimal amount RAM that you want to give to server*
  - MAX_RAM = 2G *- maximal amount RAM that you want to give to server*
  - TZ = Europe/Moscow *- built-in feature in Debian - required timezone*

### Exposed Ports
  - 25565 *- standard Minecraft port*

### Mounted Volumes
  - /data *- contains every single file of your server*

# Best usage
For easiest usage of this image, I recommend you to use my manage script. It is available [**here**](https://github.com/Project-Sixth/DOCK-5A3/blob/master/manage.sh), at my GitHub. After you download my script (for example, you can use command `curl -sL https://raw.githubusercontent.com/Project-Sixth/DOCK-5A3/master/manage.sh > manage.sh; chmod +x manage.sh`), just follow next steps:
  1. Place script in any convinient place and make it executable (`chmod +x manage.sh`)
  2. Edit it with any editor and change mount directory to anywhere you find nessesary.
  3. Create new container by using command `manage.sh create`
  4. If you need to stop, restart or start container - easy as executing `manage.sh start|restart|stop`
  5. You also can use `manage.sh attach` to attach to RCON console. Exiting from it is `Ctrl+p Ctrl+q` keybind
