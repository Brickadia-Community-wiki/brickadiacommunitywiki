# Omegga Brickadia Server Linux Setup Guide
[Omegga](https://github.com/brickadia-community/omegga) is a project that wraps and extends the capabilities of a normal brickadia dedicated server by additionally providing the ability to run plugins as well as providing a nice web based UI
to easily control and manage the brickadia server. 

This guide aims to show how to do a basic install using Ubuntu Linunx. The extended install and troubleshooting guide [can be found on the main project page](https://github.com/brickadia-community/omegga?tab=readme-ov-file#quick-setup-automatically-download-launcher)

## What you will need
### Hardware
- at least 2 CPU cores
- at least 6 GB of RAM. 

### Software
- a Linux server (either a physical server or a Windows 11 machine running WSL will work) with Ubuntu installed
- a user in the server who is **NOT** root. 

## Instructions

### Windows WSL Specific Instructions
If you are running this via Windows 11 WSL2, you will need to add a config to the Ubuntu WSL config for you to be able to access the Web UI via localhost if you have not enabled this in the past. 

1. Open Powershell
1. Add mirrored networking to the WSL system:

    ```
    "[wsl2]`nnetworkingMode=mirrored" | Add-Content -Encoding ASCII -Path "$env:USERPROFILE\.wslconfig"
    ```

1. Turn off the WSL instance if it is running: `wsl --shutdown Ubuntu`
1. Open the Ubuntu WSL app as normal, and it will start back up, then proceed with the install directions below. 

### Installation
1. As mentioned above, verify you are not running as root and create a user if needed. 
1. Add the needed repositories for steamcmd: 

    `sudo add-apt-repository multiverse; sudo dpkg --add-architecture i386; sudo apt update`

1. Install steamcmd: `sudo apt install steamcmd`
1. Install nvm:

    `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash`

1. Activate nvm: `. ~/.nvm/nvm.sh`
1. Install node v24: `nvm install 24`
1. Install Omegga: `npm i -g omegga`
1. Create a directory for the server to live in: `mkdir omegga-server`
1. Navigate into the folder: `cd omegga server`
1. Run omegga: `omegga` and it will generate server files in the directory you are currently in, and press `Y` to the steamcmd reference request
1. The server will ask you whether you want to use username/password or hosting token authentication. Choose what you would prefer
1. Once entered, the server will start, then it will show the address of where to access the webUI. 

