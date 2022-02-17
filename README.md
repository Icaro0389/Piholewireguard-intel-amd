![Pivpn Banner](pivpnbanner.png)


**[PIVPN.IO](https://pivpn.io)** | **[DOCUMENTATION](https://docs.pivpn.io)**

 ## This is not the official repository. I change the installation script to bypass automatic installation of OpenVPN on a non PI board.
 
 ## Official Repository can be found: https://github.com/pivpn/pivpn
 
 

## About

Visit the [PiVPN](https://pivpn.io) site for more information.
This is a set of shell scripts initially developed by **@0-kaladin** that serve to easily turn your Raspberry Pi or X86/X64 Machine (TM)
into a VPN server using Wireguard.

  * [WireGuard](https://www.wireguard.com/)


Have you been looking for a good guide or tutorial for setting up a VPN server on a Raspberry Pi or Ubuntu based server?  
Run this script and you don't need a guide or tutorial, this will do it all for you, in a fraction of the time and with hardened security settings in place by default.  


This scripts primary mission in life is to allow a user to have a home VPN for as cost effective as possible and without being a technical wizard.  
Hence the design of pivpn to work on a Raspberry Pi ($35) and then one command installer.  
Followed by easy management of the VPN thereafter with the 'pivpn' command.  
That being said...


## Prerequisites

To follow this guide and use the script to setup a VPN, you will need to have
a Raspberry Pi Model B or later with, an SD or microSD card with Raspbian installed,
a power adapter appropriate to the power needs of your model, and an ethernet cable or wifi
adapter to connect your Pi to your router or gateway.  
It is recommended that you use a fresh image of the latest Raspbian Lite from
https://raspberrypi.org/downloads, but if you don't, be sure to make a backup
image of your existing installation before proceeding.  
You should also setup your Pi with a static IP address
but it is not required as the script can do this for you.  
You will need to have your router forwarding UDP port 1194 or whatever custom
port you may have chose in the installer
(varies by model & manufacturer; consult your router manufacturer's documentation to do this).
Enabling SSH on your Pi is also highly recommended, so that you can run a very
compact headless server without a monitor or keyboard and be able to access it
even more conveniently.


## Installation


**Method 1 (clone repo)**

```Shell
git clone https://github.com/Icaro0389/Piholewireguard-intel-amd.git
bash Piholewireguard-intel-amd/auto_install/install.sh
```

### How it works

The script will first update your APT repositories, upgrade packages, and install WireGuard.

It will ask which authentication method you wish the guts of your server to use. If you go for WireGuard, you don't get to choose: you will use a Curve25519 public key, which provides 128-bit security. On the other end, if you prefer OpenVPN, default settings will generate ECDSA certificates, which are based on Elliptic Curves, allowing much smaller keys while providing an equivalent security level to traditional RSA (256 bit long, equivalent to 3072 bit RSA). You can also use 384-bit and 521-bit, even though they are quite overkill.

If you decide to customize settings, you will still be able to use RSA certificates if you need backward compatibility with older gear. You can choose between a 2048-bit, 3072-bit, or 4096-bit certificate. If you're unsure or don't have a convincing reason one way or the other I'd use 2048 today (provides 112-bit security).



The script will also make some changes to your system to allow it to forward internet traffic and allow VPN connections through the Pi's firewall. When the script informs you that it has finished configuring PiVPN, it will ask if you want to reboot. I have it where you do not need to reboot when done but it also can't hurt.

After the installation is complete you can use the command `pivpn` to manage the server.
