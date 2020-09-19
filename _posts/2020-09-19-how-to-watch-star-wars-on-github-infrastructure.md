---
layout: post
title: How to watch Star Wars on GitHub infrastructure?
summary: Get a MacOS or Linux shell, for free, in around 2 minutes with fastmac
date: 2020-09-19T11:27:15.983Z
---
In the past months I have been playing around with [GitHub Actions](https://github.com/features/actions). The possibilities with them seem endless. Most of the projects that I contribute to now are using them as a CI system. It's pretty cool and easy to setup. 

I recently found the project [fastmac](<https://github.com/fastai/fastmac >). Basically the project is:

> Get a MacOS or Linux shell, for free, in around 2 minutes

It's useful if you are curious to see what is included in the images provided by GitHub.

Let's see how this works? The instructions are pretty easy to follow:

![fastmac demo](/assets/uploads/fastmac.gif "fastmac demo")

1. Fork the repository
2. Got on the Actions tab of your fork
3. Choose the shell that you want in the workflow list: mac or linux
4. Press `Run workflow` on the master branch
5. Once it starts click on it and go in the build section
6. Unfold the `Setup tmate session` section 
7. Once you get a log with WebURL and SSH that's it!

```
WebURL: https://tmate.io/t/qcpWn4M2FLzLmChE7ucPHxKFW
SSH: ssh qcpWn4M2FLzLmChE7ucPHxKFW@nyc1.tmate.io
```

You can now open a new tab or a terminal and access via SSH the image that you chose. You can start investigate what is in the image provided by GitHub!

Now the question that **EVERYONE** wonders.

> Can I watch Star Wars from GitHub's infrastructure?

![Star wars logo](/assets/uploads/starwars.png)

Let's see what does the image provides me. Do I have the command `telnet`?

```
runner@fv-az50:~/work/fastmac/fastmac$ whereis telnet
telnet: /usr/bin/telnet.netkit /usr/bin/telnet /usr/share/man/man1/telnet.1.gz
```

Yeay!

Ever heard of [Star Wars over telnet](https://lifehacker.com/watch-star-wars-in-text-via-telnet-373571)? The movie was reproduced in [ASCIIMATION](http://www.asciimation.co.nz/) and watchable via telnet.

Let's try it!

```
runner@fv-az50:~/work/fastmac/fastmac$ telnet towel.blinkenlights.nl
```

![Star Wars Asciimation](/assets/uploads/starwars_asciiart.png)

😍 See you in 121 minute! (the actual animation is ~20 minutes)

⚠️ Don't forget to \`Cancel workflow\` once you are done having fun.