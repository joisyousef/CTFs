First I run nmap:

![](attachment/af7f9c5dd63d0240ea12606259d795e6.png)

I set up a listener on port 9999 to that IP:

![](attachment/c1b41d696e62f78f8dbdde9a9e0139a3.png)

and opened it on a browser:

![](attachment/5e5ac3510ec43c0c6f08f4993a86065f.png)

and on port 10000 I found this page:

![](attachment/42aa7431cde8363c53303a27010fd4f3.png)

I run dirb on it:

![](attachment/6f73c6879166105bf2f9ab0989ef65bd.png)

I found a **/bin** subdirectory:

![](attachment/6bcd79d71a7d099c5aa18a177507e0ff.png)

I downloaded the file and transferred it to my windows machine to debug it on immunity debugger