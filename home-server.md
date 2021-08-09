# Building Your Home Server

Have some old laptops lying around collecting dust? 
Are they too old to run the latest Windows or softwares? 
Fret not, there are many interesting side projects that you can embark on with these old laptops!

## Step 1: Choosing your OS

You will likely want to choose one of the linux flavour for this.
For my own server setup, I decided to choose Debian 10.

## Step 2: Issues After Installation

There could be multiple issues faced after installing your OS.
Jotting down some of the issues I faced & how I solved them.

### 2.1: Unable to connect to internet

Connecting to internet is not so straightforward without a desktop GUI.
You would need to add the following into `/etc/network/interfaces` as described [here](https://askubuntu.com/questions/330093/cant-connect-to-a-wired-connection)

```
auto eth0
iface eth0 inet dhcp
```

Note that I am assuming eth0 is your networking device. Use `ip addr` to identify the name of your networking device.
Finally, restart your networking service.

```
systemctl restart networking
```

### 2.2: Sudo doesn't work

Note that sudo doesn't come with Debian by default, so you would have to install it.

```
apt-get install sudo
```

Then grant relevant user access to sudo by adding the following at the end of `/etc/sudoers` file

```
username  ALL=(ALL) NOPASSWD:ALL
```

### 2.3: Server Date Wrong

Use `date -R` to determine your server's date and time. If it's off, follow instructions [here](https://wiki.debian.org/NTP)

## Step 3: Potential Softwares Required

### 3.1: Git

```
sudo apt-get install git-all
```

### 3.2: Docker

- Docker Engine is the open source containerization tool for containerizing your application. To install, follow instructions [here](https://docs.docker.com/engine/install/debian/)
- Docker Compose is a tool used to run multi-container Docker applications. To install, follow instructions [here](https://docs.docker.com/compose/install/)

## Step 4: Desktop Environment

### 4.1: Installing Desktop

There are many options to choose from if there is a need for a desktop GUI. Refer [here](https://wiki.debian.org/DesktopEnvironment) for more details.

### 4.2: Google Chrome

Follow steps [here](https://linuxize.com/post/how-to-install-google-chrome-web-browser-on-debian-10/) to install Chrome

### 4.3: Teamviewer

Follow steps [here](https://linuxize.com/post/how-to-install-teamviewer-on-debian-10/) to install Teamviewer

## References

Other people's project
- [How I turned my old laptop into a server](https://dev.to/jayesh_w/this-is-how-i-turned-my-old-laptop-into-a-server-1elf)
