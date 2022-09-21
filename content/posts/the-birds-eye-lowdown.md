---
title: "The Bird's-Eye Lowdown"
subtitle: "Ways to monitor your system from the top"
date: 2021-09-20T16:04:48-10:00
draft: false
---
I want to know what my computer is doing.

This desire appears old-fashioned. Who cares about computers any more?

Give the people what they really want: Prometheus and Grafana charts reporting on their Kubernetes clusters! Spikes and constraints over the long term!

Not today, faithful readers. Today, we’ll just look at one machine at a time. We’ll look at its memory, what’s using its CPU, and call the processes by name.

## Remember the first time you ran ‘top’?

All top does is give you a live list of what’s running on your system and let you watch it and manage it. Pretty handy.

The simple utility `top` perhaps doesn’t get enough credit for its smooth and modern looks. Look at its clear labels and simple, to-the-point info. Its tallies are updated and presented in clear columns. It doesn’t take long to learn how to read it, and less time what keys to hit to (k)ill or (r)enice a rogue process.

If you need to sort by anything, it’s not difficult. Your needs have likely been anticipated by your friend top.

![top](https://bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com/public/images/ba77d7d6-9d81-4b8c-a582-0c395c32ec68_984x682.png "classic `top`")

Compare this interactive program to tools like iostat and vmstat. They produce useful and detailed information, but…top is so much easier to get that quick snapshot.

What more could anyone possibly need?

## Hat Tip to htop

Until this year, I wasn’t aware of the thriving stable of programs which try to do better than good ole ‘top’. The first flashy one that caught my eye was [htop](https://htop.dev/). I am not sure what the h is for. We aren’t talking about graphical system monitor tools here, but htop sure wants to give us the best of both worlds.

![htop](https://bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com/public/images/c1617e99-7533-452f-abb6-0462ed78b08f_984x641.png "`htop`")

We have color! We have all 8 of my (hyperthreaded) CPU cores! We have user-friendly F-key menus.

It is pretty. But for good or ill, it appears to be just, you know, top with some flourishes. I like the idea of color coding processes to group them at a glance (blue low priority, green normal user, red kernel). Is it enough, though?

## Did you say “at a glance”?

The next trendy top-like tool is called “ [glances](https://nicolargo.github.io/glances/)”. How many glances is this going to take? That’s what I wonder.

![](https://bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com/public/images/9b6d0a02-1cfd-494c-a976-77de9aa7704b_1614x785.png "`glances`")

Can you see all of that, or did I make my Terminal too big? These modern pretty programs just make me want to gobble up the screen! (I remember a classmate opining that the real purpose of a GUI was to have more and more xterms open. Really, though—was he wrong?)

Still—I like glances because it sums things up for me. I honestly don’t need to know how each of my CPU cores is doing, unless it’s via blinkenlights built into the case. And see how it keeps track of my containers? Aw! And all of the networks, including microk8s’s. This seems really organized and could probably be customized to be every better for my personal “at a glance” readout. I’m intrigued.

## Eh, top! atop of spagheeeeetti

I fired up another tool trendy with the sysadmins, I mean DevOps Engineers. It’s called [atop](https://haydenjames.io/use-atop-linux-server-performance-analysis/) and it appears to know everything.

![atop](https://bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com/public/images/219d5bf5-4e66-4363-8537-923fac204899_1119x790.png "`atop`")

I mean, okay, I get some of that. It’s probably very clear and functional once you know what some of the abbreviations mean. I may regret saying this—maybe atop will someday be my favorite tool ever, no cutesy tomfoolery—but right now I get tired just looking at it. Sorry, atop. I never gave you a chance.

## Name dropping: my uncle is a famous shell

The fanciest yet? It’s bashtop, I mean [bpytop](https://github.com/aristocratos/bpytop), or maybe btop++? Bpytop we remember, of course, from the epic Rush song in which Bpytop attempts to escape the single Linux system he runs on and emerge onto a higher level of abstraction, among the k8s Pods.

In a similar fashion to the song, this monitoring tool might be doing just a little bit too much.

Here are two versions of it—one entirely in bash, the other in python. It’s hard for me to tell them apart. Can you?

![](https://bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com/public/images/29edde16-9890-4b09-9aee-0f47e100d404_1614x826.png "I’ll let you guess")

![](https://bucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com/public/images/7d977895-50f0-4322-8423-95055dd83e28_1119x790.png "Also a mystery!")

I’m drawn to them both, even as I’m repelled by their shameless GUI elements. They’re very pretty! Will they work with my Switch controller?

But yeah, maybe I DO want to know this stuff on some remote machine. I’m trying not to be a big cynic. All this visualization is some very clever and careful work. It seems like the sort of thing you aren’t sure about at first, but after a while you can’t imagine living without it. We’ll see!

## Favorite?

I want to try out all of them in a work environment and see which clicks. With only a few hours so far using each, I think I’m most enamored of glances.

(I have completely skipped the “like top, but runs in Node” subgenre of these tools. But please know they exist, so you too can wonder at our mysterious world.)

Any opinions?

