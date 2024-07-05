First I done nmap scan

![](attachment/60ac3a82f3b658140988d55c41a248cb.png)

on port 80 I found the default web page of apache

then I run **dirbuster to seek for the directories**

and got directory called content:

![](attachment/55dfdf54cc0465350fe1ecaf90116597.png)

![](attachment/a74f1bca4c7e80f5f8f040c4a0029096.png)

then I run gobuster again on content subdirectory

![](attachment/356ce009f490683fe898b246a3fa4766.png)

and found a login page!!! in /as but I did not have the credential

![](attachment/22379c249ab5bb6df38ca9aaeb6ffc52.png)

so I checked /inc and found a backup folder with sql

![](attachment/aec1cf7b0e394d6a1881a6c88dc0d4c6.png)

I cat out the content and found a username and hash

![](attachment/42d649f24959779187f487c13fde8e5f.png)

then I cracked this hash

![](attachment/204619cfdb8ae1b2841afdd174627f13.png)

then I logged in with:

manager:password123

![](attachment/051046c01787fffd5a8f6179667025e8.png)

then I switched the first box to running as said in /content

then I refreshed the /content page and:

![](attachment/35afd1a34e5b3ce5cfc8ca5784d4972c.png)

in the ADS section I found this:

![](attachment/8889224d08d88ccf70daf66354700da5.png)

and uploaded the reverse shell and opened a netcat listener

and the file of the reverse shell is uploaded here:

![](attachment/727a616d593fda3898bb4465138200e0.png)

then I got a shell!!!

![](attachment/1359d9883641807dc3b0bea84fdd410f.png)