![](attachment/f41bed6af81faf8fd1b9a9b920b0a8f2.png)

then I run dirb to find directories and found **/secret**

![](attachment/3d865514f0137d165a9f939329cb9a4e.png)

and I visited it and downloaded a text file:

![](attachment/48fda0d9c7f236ec20a847df52713d0a.png)

!!!!!!!!!!!!!!!!!!!!!!!!!!!!what!!!!!!!!!!!!!!

then of course port 53 is open for dns for a reason

  

![](attachment/af04b06bd3ef26ee6295b34ef6fa5212.png)

![](attachment/066b4858847eeb6db47cf6b15583cc2f.png)

I edited “192.168.133.137 blackpearl.tcm”

then I reload firefox with “blackpearl.tcm” and this page showed up

![](attachment/54ae9a15ab2f405c82c718bb694e497c.png)

I ran ffuf one more time but on blackpearl.tcm this time

![](attachment/edd68f8abb586e8c94d6206e15bfdca9.png)

![](attachment/172e56734e0a239bf8e3f6b5c6fd04bc.png)

![](attachment/3872bf24d1526e72d0df0250cc0df699.png)

![](attachment/8a26d4eb755afe162567f1537a806c1f.png)

![](attachment/f899f3f2e3eb3a104661df70e6753582.png)

![](attachment/0c55aa6e2f080e1ee57111a08c443acb.png)

so we must privilege escalate this shell

![](attachment/dcf0010837c7f6dd6ddd2d2bcd72f99c.png)

with the use of linpeas:

![](attachment/76a5d4c8ab153d5874caed39c54f06cf.png)

![](attachment/5dd8daa9f77575aee309294bb06ff970.png)

with the use of gtfoopens.com:

![](attachment/af741f6d3d8a8f3a1666112b171ffafe.png)

![](attachment/c4e20858e6ec722f733998e664fc1e9a.png)

finished#######################################