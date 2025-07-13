# Dedicated Servers

With the release of Brickadia on Steam, the dedicated server files are no longer gotten from the main brickadia website.
Instead, these are now downloaded either directly from steam or anonymously from [Steamcmd](https://developer.valvesoftware.com/wiki/SteamCMD) using appid `3017590`.

Note that you will still need to supply the dedicated server a server hosting token by passing it the `-token=yourtokenhere` executable argument. Once the token is registered to the server for the first time, the `-token` argument can be omitted in future runs of the server executable. 

Servers currently use **udp port 7777**. This can be changed if needed by supplying and modifying the `-port=7777` argument to your desired port. 

In some circumstances (such as hosting multiple servers in the same VM/Container) you may want to change the location of the Dedicated Server's `Saved` directory (`~/.config/Epic/Brickadia/` by default). This can be done using the `-UserDir=PathToSavedDir` argument.

## Dedicated Server Commands
These commands can be used directly in the terminal where the dedicated server is running. 


| Description | Command |
| ------------ | ------------- |
| grant self/player admin | `Chat.Command /GrantRole Admin [Your username here]` |
| Load map from mapfile name | `BR.World.Load "map name"` |
