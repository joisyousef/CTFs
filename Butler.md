First I run nmap:

![](attachment/56dd9929700ca54b697e8c51be43a2e0.png)

I got port 8080 is open and hosting a login page for JENKINS

![](attachment/ba0d2bad18c00a4142d3bc436462b071.png)

then I enumerated a lot and got nothing so I got lucky when I searched for jenkins default password: **admin/password**

bur it does not work unfortunately

![](attachment/7502bf04938fc6527e7caf9bd979a314.png)

---

so I tried burpsuite

I enabled foxyproxy and then I tried to log in to jenkins again with **admin/password** I know it will not work

![](attachment/6de85f0ebcead93b565257add34d4b30.png)

I sent the above to intruder and repeater

![](attachment/23fddf598e33f741e34cf94ebe1e654f.png)

![](attachment/fc68b19f7093e06e21d72440d1045641.png)

I tried brute force attack on it and found a login credentials: **jenkins/jenkins** and I got in!!!!!!!!!

![](attachment/5c1f44b4b00deb788bdeda45381db485.png)

and in manage Jenkins there is a script console in groovy

so I searched for reverse shell in groovy and implemented this reverse shell:

[https://gist.github.com/frohoff/fed1ffaab9b9beeb1c76](https://gist.github.com/frohoff/fed1ffaab9b9beeb1c76)

![](attachment/5f52c34f326602ee6c6b3815cfde896c.png)

and I run the script while I was setting up a netcat listener

![](attachment/47677d298cef6301b01bbae52317f398.png)

and I got a shell!!!!!!!

and I moved **winpeas** to the machine and run it!!!!!!!!!!!!

![](attachment/c850c7951f3f9463a387b3cc3ac84294.png)

then I created a malware with msfvenom and transfered the file to the butler machine

![](attachment/9bf1e87817e912179d470b4658761a9e.png)

![](attachment/25e942fc8efe7a53a2ac64be3b93e95a.png)

see!!!!!!

so first I stopped the service running

```Lua
 sc query WiseBootAssistant
```

![](attachment/291c235c69991701ceb85f3442f2b3f4.png)

```Lua
sc start WiseBootAssistant
```

![](attachment/a2f2513c9a04acc48c409cc0e6595fb5.png)

and I got a shell with root!!!!!!!!!!!!!!

![](attachment/bf3061f1a05ec300a080643747190050.png)