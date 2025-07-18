# Linux Dedicated Server Guide
So you want to use a linux server but dont know where to start? This guide is for you.

*(Note for ARM server runners: You cannot currently use Box64 for ARM servers as the latest server version relies on features [Box64 does not yet support](https://github.com/ptitSeb/box64/issues/2808))*

## Prereqs (Steam Early Access Edition)
You will need:

- a linux X86_64 VM with a recent CPU with 2-4 cores
- at least 2 GB of RAM. 
- steamcmd
- a copy of brickadia
- ability to port forward udp port 7777
- a public IP address

## Instructions
1. Log in to your linux VM and install [steamcmd](<https://developer.valvesoftware.com/wiki/SteamCMD#Linux>)
    1. Note: if you prefer a distro agnostic method, just create a directory to hold steamcmd, `cd` into it, then run `curl -sqL "https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz" | tar zxvf -` to grab steamcmd. be sure to install the needed `lib32gcc-s1` library from your package manager. 
1. Create a new folder somewhere to house the game files. 
1. Create a file called `update-brickadia.sh`, then run `chmod +x update-brickadia.sh` on it to make it executable. 
1. Open the file with your favorite editor and put the following:
``` bash
#!/usr/bin/env bash
/path/to/steamcmd/steamcmd.sh +force_install_dir /your/install/directory +login anonymous +app_update 3017590
```
    - Be sure to replace `/path/to/steamcmd/` with whatever path the steamcommand shell script lives at. 
    - Also be sure to replace `/your/install/directory` with wherever you want the game files to live.
1. Run the `update-brickadia.sh` script. It should install the brickadia server to the path you set above. You can re-use this script in the future to update the server when needed.
1. Once the download finishes, you'll be dropped to the steamcmd shell, you can just type `exit` here. 
1. Inside of the install directory you set earlier, you will now have files. One of which is the folder `Brickadia`
1. Go inside `Brickadia/Binaries/Linux`, and you should see the file `BrickadiaServer-Linux-Shipping`, this will be what we will use to launch the server in a bit. 
1. Go to <https://brickadia.com/account> and login, then generate a server hosting token and copy this somewhere.
1. Back in the vm in the directory with the server launcher binary mentioned earlier, run the following command: `./BrickadiaServer-Linux-Shipping -log -port=7777 -token=yourTokenHere`
1. This will spin up the server, and after about 2 minutes it should be fully loaded.
1. Connect to your dedicated server via manual connection in game. then go to Menu -> Edit Game and set up the server options and save them.
1. In the linux environment, hit ctrl+c to stop the server.
1. Run `cd ~/.config/Epic/Brickadia/Saved/Config/LinuxServer` to drop into the folder  with the server config files.
1. Edit `GameUserSettings.ini`  to set your server name, password, etc until you are happy with it. 
1. Verify in your network port `7777` udp is port forwarded so that others can connect. 
1. Once the network is in place, go back to the directory with `BrickadiaServer-Linux-Shipping` in it. 
1. Since we have already registered the token to the game server, we can now just run the server with `./BrickadiaServer-Linux-Shipping -port=7777 -log` going forward. Do this now. 
1. Open up Brickadia and connect to your server by hitting Join Game -> Connect Manually.
1. You should now be connected, and the server is up!

## Post-Setup Configuration Tips
#### Enable Auto Save
1. In your server console, type `BR.World.SaveAs savename` (where savename is what you want the name of your save to be). This will create your save file for the server. 
      - Note: If you do not run this command, the Auto Save won't function.
      - If you already created a save file for your server, you can skip this step.
2. Connect to your server in game, press the escape key to open the menu -> edit game
3. Click the advanced settings toggle at the top left of the menu
4. Scroll to the bottom and enable Auto Save. You can also configure save interval and announcing of the saves.
5. Whenever you restart your server, you will need to run `BR.World.Load savename` to have the server reload the save file.
