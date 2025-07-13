# Dedicated Servers

With the release of Brickadia on Steam, the dedicated server files are no longer gotten from the main brickadia website.
Instead, these are now downloaded either directly from steam or anonymously from [Steamcmd](https://developer.valvesoftware.com/wiki/SteamCMD) using appid `3017590`.

Note that you will still need to supply the dedicated server a server hosting token by passing it the `-token=yourtokenhere` executable argument. Once the token is registered to the server for the first time, the `-token` argument can be omitted in future runs of the server executable. 

Servers currently use **udp port 7777**

## Dedicated Server Commands
These commands can be used directly in the terminal where the dedicated server is running. 

- grant yourself or another player admin:
    - `Chat.Command /GrantRole Admin [Your username here]`
- Load a map from the installed map list:
    - `BR.World.Load "map name"`