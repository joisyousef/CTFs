First I run nmap scan:

![](attachment/febf6d8f2b95860b2e57650729de389a.png)

so I searched for **apache jserv (protocol v1.3) exploit** because it seems interesting

so I found exploit: [https://www.exploit-db.com/exploits/48143](https://www.exploit-db.com/exploits/48143)

![](attachment/ffe17c43dc8c681c32b824910f65cdf5.png)

I download it and run it:

![](attachment/fa919c8dd3bc2e633bd6edd6ba782cfd.png)

and found a **username and a password!!!!** so I logged in with them and I got a shell!!!:

![](attachment/9c5bb10c17db7148652d24024da8cfdd.png)

I run history:

![](attachment/ea2c0daf73051488633b84caca23d964.png)

I found these two files:

![](attachment/d4df7ebf77d2007e6dc7fc9b5024d242.png)

then I transferred them to my machine:

![](attachment/d720197f12cab38c6e8ff8090265e005.png)

then I searched how to crack **.asc** file:

![](attachment/c2fde662facb48770a1ceda72cba781e.png)

![](attachment/510a800c41b52704108db755755a5f4d.png)

then I cracked the hash that came out:

![](attachment/b421f8dde38a081eba512d661a18d5ce.png)

**alexandru is the password to crack the .pgp file:**

![](attachment/a78afe6df909cf8d497885ca4eae8688.png)

![](attachment/79dd962e1285628701dda06496321134.png)

and I can decrypt it now:

![](attachment/04ccca2f6250f603464f48b912ae82cf.png)

and I got this long password for merlin then I tried to ssh with these credentials and I got a shell of merlin:

![](attachment/fcefdc6d506d00bfe8bb29fb15fea631.png)

then i found a vulnerability:

![](attachment/1ec0dff87cc90609673a2cb6f2bd079d.png)

on gtfobins:

![](attachment/62e64a55eeef5539e903c1835ae95f66.png)

![](attachment/ed52d830ae1225e2331705491fc17f14.png)

and I got root!!!!!!!