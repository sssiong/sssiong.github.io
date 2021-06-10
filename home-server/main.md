# Building Your Home Server

Have some old laptops lying around collecting dust? 
Are they too old to run the latest Windows or softwares? 
Fret not, there are many interesting side projects that you can embark on with these old laptops!

## Step 1: Choosing your OS

You will likely want to choose one of the linux flavour for this.
For my own server setup, I decided to choose Debian 10.

## Step 2: After Installation

There could be multiple issues faced after installing your OS.
Jotting down some of the issues I faced & how I solved them.

### 2.1: Sudo doesn't work

Note that sudo doesn't come with Debian by default, so you would have to install it.

### 2.2: Unable to connect to internet

Connecting to internet is not so straightforward without a desktop GUI.
You would need to add the following into `/etc/network/interfaces` as described [here](https://askubuntu.com/questions/330093/cant-connect-to-a-wired-connection)

```
auto eth0
iface eth0 inet dhcp
```

Note that I am assuming eth0 is your networking device. Use `ip addr` to identify the name of your networking device.
Finally, restart your networking service.

```
sudo systemctl restart networking
```

## References

Other people's project
- [How I turned my old laptop into a server](https://dev.to/jayesh_w/this-is-how-i-turned-my-old-laptop-into-a-server-1elf)
- 
