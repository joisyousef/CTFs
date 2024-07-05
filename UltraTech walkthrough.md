First I did nmap scan

![](attachment/5e6fcabc682de7c83250c26a034ce605.png)

8081

![](attachment/a04bac4ee8955ec7960814bfd3d931be.png)

31331

![](attachment/d7079067526f4f88cb5321f624858f52.png)

but first I navigated to:

![](attachment/0ee356449bc59c4f1e3a279ce6083797.png)

![](attachment/5891f8a2d703932553b95952ad8189f6.png)

and then I found a login page

![](attachment/5a1c0be54cbde7a709c9a9912fc601bf.png)

  

i found some files in this site but I used dirb

![](attachment/da771f16b86586de364921c5696c3f6b.png)

![](attachment/0e3567de9defbfdb2e758359fd98c86f.png)

const url = `http://${getAPIURL()}/ping?ip=${window.location.hostname}`

so this code can be edited and do a ping command on hte ip they gave me

![](attachment/5c5eb5d5efd2ed6038d143e87a282fbf.png)

then I edited the command to be OS command injection

![](attachment/8c1cef1474b60fc4461d4cd34f5cf7d0.png)

and I found a file!!! and cat it out

and found hashes for r00t and admin users:

![](attachment/25d7bae16338085a859904ec072d0a59.png)

and I cracked the hashes with crackstation.net

![](attachment/b581f6483c19eb8a0fe46cc8c46358c9.png)

then I tried to connect via ssh with the credentials i found and it worked and got a shell!!!

![](attachment/29ebf7559af923fafc92cb4ca05b1c25.png)

![](attachment/522ecb771d8da820564885458a48e0f4.png)

![](attachment/f13b09c2dba646569c70c8411c48db59.png)

![](attachment/e5844cf4044b75b0df3683e9e9725dfc.png)

and I got root!