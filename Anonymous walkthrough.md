First I run nmap:

![](attachment/5b2af9c73e6676ecd2a2db38463f5311.png)

I found anonymous ftp login allowed so I tried to connect and found a file called **scripts**

![](attachment/1cffc3ca2e96d30fd36ea1deac38fee7.png)

then I downloaded the file

```Less
wget -m ftp://anonymous:anonymous@10.10.223.95
```

![](attachment/c0bdb092bf6eb06d794a78752104c310.png)

and found three files so I cat them out:

![](attachment/d54a305ed24a40e20e526e8e15eab033.png)

![](attachment/c93952e00c579c7ce3a09f0168a7353a.png)

![](attachment/579207004b996635cbf2c324ece51ed9.png)

![](attachment/e64fce4f3b60a63a4ec35fd335e04950.png)

and the [clean.sh](http://clean.sh) is writeable file and running /bin/bash so I can replace it with a shell!!!

![](attachment/9d2314ad7256a6c49371e6fbe21a55b9.png)

and I did I put one liner reverse shell and replaced the file with ftp

![](attachment/947f89b78d745d5d810d604c308ba5a3.png)

and opened a netcat listener and waited one minute for the file to execute I expected the file is cron jop execeuting every minute and I got a shell!!!

![](attachment/9d924db088b04b40ee65a3d5565e860a.png)

and found the first flag:

![](attachment/6e50670282198d5230867740243c2b29.png)

---

```Less
sudo -l
```

![](attachment/b28215584eb1219db87e88fddf7be55b.png)

then I searched for a tty shell on google:

```Less
python -c 'import pty; pty.spawn("/bin/bash")'
```

![](attachment/b659c843171ab392d65fcec60b2149bb.png)

and this time is asking for a password! so it does not work

so I tried with **suid:**

```Less
find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null
```

![](attachment/86e88473e90b00fb1ae15e09402c2104.png)

and I tried to search a lot in gtfobins and found /usr/bin/env:

![](attachment/ae2bde136c186daafec19590255ae255.png)

```Less
/usr/bin/env /bin/bash -p
```

![](attachment/941fc04f914348ab13b8438b68825292.png)

and I got root!!!!!!