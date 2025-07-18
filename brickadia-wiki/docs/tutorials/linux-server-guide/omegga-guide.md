# Omegga Brickadia Server Linux Setup Guide
[Omegga](https://github.com/brickadia-community/omegga) is a project that wraps and extends the capabilities of a normal Brickadia dedicated server by additionally providing the ability to run plugins as well as providing a nice web based UI
to easily control and manage the Brickadia server. 

This guide aims to show how to do a basic install using Ubuntu Linux. The extended install and troubleshooting guide [can be found on the main project page](https://github.com/brickadia-community/omegga?tab=readme-ov-file#quick-setup-automatically-download-launcher).

## What you will need
### Hardware
- at least 2 CPU cores
- at least 2 GB of RAM

### Software
- a Linux server (either a physical server or a Windows 11 machine running WSL will work) with Ubuntu installed
- a user in the server who is **NOT** root. 

### Installation
1. As mentioned above, verify you are not running as root and create a user if needed. 
1. Install lib32gcc-s1: `sudo apt install lib32gcc-s1`
1. Install nvm:

    `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash`

1. Activate nvm: `. ~/.nvm/nvm.sh`
1. Install node v24: `nvm install 24`
1. Install Omegga: `npm i -g omegga`
1. Create a directory for the server to live in: `mkdir omegga-server`
1. Navigate into the folder: `cd omegga-server`
1. Run omegga: `omegga` and it will generate server files in the directory you are currently in
1. Press `Y` to install steamcmd
1. The server will ask you whether you want to use username/password or hosting token authentication. Choose what you would prefer.
1. Once entered, the server will start and will show the address of where to access the webUI. 

**For WSL users, you ^^must do the following^^ to access the web UI:**

1. Type `/stop` to stop the server if it is running
1. Install wsl2binds with `omegga install gh:Meshiest/wsl2binds`
1. Launch omegga once more with `omegga`
1. If you get a Windows Firewall prompt for udpprox.exe after starting the application, just click `Allow`
    - If you need to connect from your computer to a different server running the omegga web UI, you may need to run the *netsh interface portproxy* command the tool generates in the console as admin to apply the needed connection rule. 
1. Your omegga server will now display a usable web UI address you can open. 