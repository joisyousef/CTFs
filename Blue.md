first I ran nmap:

![](attachment/ece8087347b6576de9a33b9faa39f076.png)

found Windows 7 Ultimate 7601 Service Pack 1 and searched on it in the exploit database and found (EternalBlue)

[](https://www.notion.soundefined)

![](attachment/e8a946fb4b59bedceaa3f94f37d5d7cb.png)

I used two auxluaries

  

1- windows/smb/ms17_010_eternalblue

2- scanner/smb/smb_ms17_010

  

then I set the rhost for both to 192.168.133.131 and exploited the machine

![](attachment/75d9e4ada74004e8de8700c46ec2b335.png)

---

I searched for EternalBlue for manual exploit on github

https://github.com/3ndG4me/AutoBlue-MS17-010

I installed the above tool

![](attachment/37b0ed35f49b4748e0d9ecb08f098675.png)

I followed its instructions and got multi_handler:

![](attachment/e773ef200d39156c431da704756f4aa2.png)