---
layout: post
title: Installing OpenVPN on Feodra 25
---
Recently I switched over from Ubuntu to using Fedora 25.

I will here outline the steps to install and run OpenVPN on Fedora:

1.Go to Activities tab and select the Terminal option to open a new Terminal.
2.In the terminal type : sudo dnf install openvpn*.
3.You might get the following error for failed dependencies:
  Failed dependencies:
    lsb >= 4.0 is needed by google-chrome-stable-33.0.1750.149-1.x86_64
    libXss.so.1()(64bit) is needed by google-chrome-stable-33.0.1750.149-1.x86_64
 The fix for which is suggested here :
 https://www.unixmen.com/fix-google-chrome-dependencies-installing-via-rpm-package/
 
 4. cd to the folder where you want to keep your config file,e.g. in this case ovpn directory in the /home folder 
  (For new users type in the terminal
      mkdir ovpn
      cd ovpn )
 5.In the ovpn folder place your ovpn file. Freely available ovpn files can be obatined from here
 http://www.vpnbook.com/freevpn
 
 6.Edit your file to add the following lines:
 script-security 2
up /etc/openvpn/update-resolv-conf.sh
down /etc/openvpn/update-resolv-conf.sh

7.To use the update-resolv-conf option we need to download and install:
http://roy.marples.name/downloads/openresolv/openresolv-3.9.0.tar.xz

8.To install openresolv extract the downloaded folder into some destination folder.Within this folder run 
  ./configure
  make
  sudo make install

9.openresolv also needs to be accompanied with helpers to resolve dns,hence install inbound (sudo dnf install inbound*)

10.Download the update-resolv-conf.sh script available at (https://github.com/masterkorp/openvpn-update-resolv-conf/blob/master/update-resolv-conf.sh) and place it in the /etc/openvpn folder

11.From the terminal type:
 sudo openvpn --config path-to-profile --http-proxy proxy port stdin
 
 Type the proxy username and password and if all settings are correct then you will end up with the statement "Initialisation Sequence Completed" at the terminal.
 
 Tips: You might have to edit resolv.conf( sudo vi /etc/resolv.conf ) to edit the nameserver to 8.8.8.8(the google's dns server )
 To know more refer to :https://wiki.archlinux.org/index.php/OpenVPN
