# Linux Dedicated Server Guide
So you want to use a linux server but dont know where to start? This guide is for you.

*(Note for ARM server runners: You cannot currently use Box64 for ARM servers as the latest server version relies on features Box64 does not yet support)*

## Prereqs (Steam Early Access Edition)
You will need:

- a linux X86_64 VM with a recent CPU with 2-4 cores
- at least 6 GB of RAM. 
- steamcmd
- a copy of brickadia
- ability to port forward udp port 7777
- a public IP address

## Instructions
1. log in to your linux VM and install [steamcmd](<https://developer.valvesoftware.com/wiki/SteamCMD#Linux>)
    1. note: if you prefer a distro agnostic method, just create a directory to hold steamcmd, `cd` into it, then run `curl -sqL "https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz" | tar zxvf -` to grab steamcmd. be sure to install the needed `lib32gcc-s1` library from your package manager. 
1. create a new folder somewhere to house the game files. 
1. create a file called `update-brickadia.sh`, then run `chmod +x update-brickadia.sh` on it to make it executable. 
1. open the file with your favorite editor and put the following:
``` bash
#!/usr/bin/env bash
/path/to/steamcmd/steamcmd.sh +force_install_dir /your/install/directory +login anonymous +app_update 3017590
```
    - be sure to replace `/path/to/steamcmd/` with whatever path the steamcommand shell script lives at. 
    - also be sure to replace `/your/install/directory` with wherever you want the game files to live.
1. run the `update-brickadia.sh` script. it should install the brickadia server to the path you set above. you can re-use this script in the future to update the server when needed.
1. once the download finishes, you'll be dropped to the steamcmd shell, you can just type `exit` here. 
1. inside of the install directory you set earlier, you will now have files. One of which is the folder `Brickadia`
1. go inside `Brickadia/Binaries/Linux`, and you should see the file `BrickadiaServer-Linux-Shipping`, this will be what we will use to launch the server in a bit. 
1. go to <https://brickadia.com/account> and login, then generate a server hosting token. copy this somewhere. 
1. back in the vm in the directory with the server launcher binary mentioned earlier, run the following command: `./BrickadiaServer-Linux-Shipping -log -port=7777 -token=yourTokenHere`
1. this will spin up the server. after about 2 minutes it should be fully loaded. 
1. connect to your dedicated server via manual connection in game. then go to Menu -> Edit Game and set up the server options and save them. 
1. in the linux environment, hit ctrl+c to stop the server.
1. run `cd ~/.config/Epic/Brickadia/Saved/Config/LinuxServer` to drop into the folder  with the server config files. 
1. Edit `GameUserSettings.ini`  to set your server name, password, etc until you are happy with it. 
1. verify in your network port `7777` udp is port forwarded so that others can connect. 
1. Once the network is in place, go back to the directory with `BrickadiaServer-Linux-Shipping` in it. 
1. since we have already registered the token to the game server, we can now just run the server with `./BrickadiaServer-Linux-Shipping -port=7777 -log` going forward. Do this now. 
1. Open up Brickadia and connect to your server by hitting Join Game -> Connect Manually
1. you should now be connected, and the server is up!