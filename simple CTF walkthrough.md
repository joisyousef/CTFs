First I run nmap

![](attachment/094a2ec2a1fe4fb7fbc2b8da2b2cb4ea.png)

First, let’s just browse to the IP and see what we get.

![](attachment/d61c8341b426061ee3aa9adfb977b1ec.png)

Next, we can use **gobuster** to scan the website for any additional pages.

![](attachment/c0aba60639ee5b80eada884d309e06f7.png)

gobuster was able to find there is a webpage at “/simple”. Let’s try browsing to it now and see what we find.

![](attachment/47d9a51ce6f8c109797a37f781d7e594.png)

The exploit is a python script so I copied and pasted into a .py document

![](attachment/63c0960893484252943ecdd37c294907.png)

Now let’s try to run it and see what we get in return

Here we can see we need to supply a URL using the -u flag and can supply a wordlist for password cracking using — crack -w

![](attachment/a1eb52bbb9390c9b50a3d38899b33b20.png)

![](attachment/3fdefba039473d9ddf625ecb11588b97.png)

Using the username and password we discovered we can now try to SSH into the target machine

![](attachment/30b787b7891856fe8ce3060dcc12161c.png)

![](attachment/92fc1ae0a5fc769b67763fb03bf7a4ff.png)

Next let’s check if any other users have home directories.

![](attachment/a340cbbcac87d38a0c185de9f0cece19.png)

---

![](attachment/e55046993ae7cc7ad29d1b0a69cd7d61.png)

With that information, let’s check out GTFOBins and see if we can use that for privesc.

![](attachment/b3d7bfaa242a33a64dc1909dc52fadb7.png)

![](attachment/ded16db8390f697489ffe6a2f14b4383.png)