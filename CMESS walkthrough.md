First I run nmap scan and found that robots.txt on port 80

![](attachment/b021e46aec6368c6d1da45edef58ef39.png)

After setting the ip tryhackme gave to me in cmess.thm in /etc/hosts, this is the site

![](attachment/a5c0b7684717a18b9b96564d4b5abd9b.png)

![](attachment/b444e6b48e75147630ce88aa4c7e92e8.png)

but nothing in these files are useful

then I tried **subdomain enumeration**

```Lua
wfuzz -c -f sub-fighter -w /home/kali/Downloads/subdomains-top1million-5000.txt -u 'http://cmess.thm' -H "HOST: FUZZ.cmess.thm"
```

I run the above first but the output was a plenty but I saw 200 word file called **dev** so I wanted to make sure the I typed this command

```Lua
wfuzz -c -f sub-fighter -w /home/kali/Downloads/subdomains-top1million-5000.txt -u 'http://cmess.thm' -H "HOST: FUZZ.cmess.thm" -hw 290
```

![](attachment/cbe1d2a0be03a9c8f34139c3c88ab338.png)

then I visited **dev.cmess.thm**

and found a chat!!! between support and andre and found a password!!!!

![](attachment/233604c13c52507bfa404d01295f6b4e.png)

I used the password with the login page I found cmess.thm/admin with these credentials

andre@cmess.thm

KPFTN_f2yxe%

and actually I logged in!!!!

![](attachment/5aa73681f75fb2f041462aa2ea65f78c.png)

then I tried to find any sort of upload file method on the site to upload a reverse shell and I found it in **content>file manager**

![](attachment/947bd9500dfa7fb7a7d2f30000f10b74.png)

and i uploaded the reverse shell but I downloaded it first from

[https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php](https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php)

**and changed the ip to my tun ip and the port to 9999**

then I searched where the file has gone to and found it in assets folder

![](attachment/9d6b1f4ef9f81f733ce0e1e5edf1fdc3.png)

I visited the url containing the file:

[http://cmess.thm/php-reverse-shell-one.php](http://cmess.thm/php-reverse-shell-one.php)

at the same time I sat a listener on my machine

![](attachment/cf0533397fe379fcd82ebfce886f925e.png)

and gained shell

and found a password!!!

![](attachment/81f869dbfa2d798fbdc7e941c8782865.png)

and with it I logged in with ssh with this password I found and username andre I found before

and found the first flag!!!

![](attachment/810103ddc54d83e0c7ee1fb7cdfd60e9.png)

and found a bug in the crontab!!!

![](attachment/5d7f111b379ad8773e3792cbac9a4468.png)

then we got roooooooooot!!!