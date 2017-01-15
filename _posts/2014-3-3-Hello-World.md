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
 
 4.
