# Frequently Asked Questions
## How do I set up a dedicated server?
See the server hosting guide.

## The server is running, but gets a "connection timed out" error when trying to connect!
Make sure that you have port forwarded UDP 7777. It is required for **dedicated servers**.

If you cannot port forward because you don't have admin credentials on your router or other blockers, you can host a server from the GUI in-game, which does not require port forwarding.

Port forwarding is a unique setup process for each router. You will probably find the best advice by searching YouTube for a video for port forwarding on your specific router.

Generally speaking, you will want to make a DHCP reservation for your computer so it always has the same IP address when it connects to your router. Otherwise, you will have to remake the
port forward each time your router decides to give your computer a new IP address. Then, you can create the port forwarding entry.

Finally, ensure that your firewall is not blocking the incoming connections.

## Brickadia is crashing on launch / the server binary is crashing on launch.
Make sure that your CPU supports AVX/AVX2. As a UE5 game, Brickadia explicitly requires this functionality on your CPU.

## Is there a list of console commands anywhere?
Not officially, but we are working to create one [here](dedicated-servers.md#dedicated-server-commands).

You can also press `` ` `` (the key usually located above tab on your keyboard) to open the console in game to see auto-completions.
Most of the commands available on the client are also available on the server console.

## How do I switch the base map?
The command is `servertravel map` where "map" is the map you want to switch to. For example, `servertravel Studio` will switch the server level to studio.

*Note:* As of writing, sometimes the `servertravel` can cause connected clients to crash. You can use `travel` to avoid this, but `travel` will disconnect
all clients before switching the server level.

## What is the default server file location?
On Linux, if you installed with `steamcmd` and didn't run `force_install_dir` to change your installation directory, `~/.steam/steam/steamapps/common/BrickadiaServer`

On Windows, if installed through the steam client, you can just right-click "Brickadia Server" -> properties -> installed files -> browse.

## Where are the server config files located?
On Linux, `~/.config/Epic/Brickadia/Saved/Config/LinuxServer/GameUserSettings.ini`

On Windows, `C:\Users\<yourusername>\AppData\Local\Brickadia\Saved\Config\WindowsServer\GameUserSettings.ini`

- A shortcut to get to this is pressing `windows key + r` to open run, then pasting `%localappdata%\Brickadia\Saved\Config\WindowsServer` and pressing ok.

## How do I add a custom world to my server?
1. Navigate to the worlds folder for your server:
    - On Linux, `~/.config/Epic/Brickadia/Saved/Worlds`
    - On Windows, `C:\Users\<yourusername>\AppData\Local\Brickadia\Saved\Worlds`
2. Drop the `.brdb` file in that directory.
3. Run `BR.World.Load "worldname"` command without the file extension.
    - For example, if your world is called `office world.brdb`, you would run `BR.World.Load "office world"` in the console.

## I just restarted my server and all my bricks are missing!
Run `BR.World.Load "worldname"`. If you do not remember your world name, you can look for it in the worlds folder for your server.

If there is no world in that directory, then you did not create a world save.

## I am running the server on Windows, and there isn't any console for me to type commands into?
Either launch the server via steam, or set the flag `-log` to the `BrickadiaServer-Win64-Shipping.exe`.
