---
title: "Why Snap instead of Docker?"
subtitle: "More about packaging and assembling Linux"
date: 2021-09-24T16:04:48-10:00
draft: false
tags: ["linux", "build and release"]
---
I don’t think I have to sell anyone on containers at this point. But for the sake of comparison, let’s go over what they give you.

1. You have your app, in a clearly defined and versioned environment (libraries, configuration, maybe a runtime like Node or Java).

2. All these pieces are defined in a text file, which lets you generate an image that’s the same every time.

3. That means you can run nearly the same thing on your development desktop as you run in testing and production environments.

4. And it means you can be very elastic—if your game suddenly needs 10 times more servers, make more based on the image as a template. If the bubble bursts, scale back down. (This assumes you’ve designed things to work in parallel.)

5. Also, it’s in its own little bottle—you only “expose” what you explicitly ask it to; for example, a Web API on port 80, but not the web server’s configuration, passwords, database info, etc.


All this magic is made possible by the image (created with Docker, Podman, or something else)—the image, in combination with the [container runtime](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) which runs the programs residing therein.

Some people seem to love containers so much that they just go ahead and ship their software on them. No more fussing about making both an rpm and a deb file and having users install it on their command line and hope the dependencies work out. No setting up special repositories to download updates. For example, [look at Amazon’s version 2 of their CLI tool.](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-docker.html) (Why isn’t [this tool](https://github.com/aws/aws-cli/tree/v2) part of every Linux distribution?) But from Amazon’s point of view, being able to grab a Docker image seems like a convenient way to run a command-line executable.

Like the [programming ecosystem package managers](https://builtation.substack.com/p/the-complete-package) and OS packaging systems, we rely upon a central repository—in this case, a [place to find and share container images.](https://hub.docker.com/)

## So What Does Snap Do?

I was wondering this myself. I had some ideas, based on the user experience. But what problems does something like a snap solve?

(I watched Canonical’s Mark Shuttleworth explain his perspective in [“Why we need a different container purely for apps”](https://www.youtube.com/watch?v=0z3yusiCOCk), or as he elaborates, “what if apt-get and docker had a bebe?”)

Installing a snap on Ubuntu can be like going to an App Store on a smartphone. It’s centralized, has pretty pictures and bits of info, and the programs are supplied and updated by their vendors rather than as part of the OS.

For a desktop user, this is pretty sweet! Compare the official installer instructions for Docker or Google Chrome. On Windows or Mac, you download and run a thing (or I guess use one of the OS-maker’s stores), and it installs, setting up lots of goodies.

On Linux, the official way is to edit some configuration files, copying and pasting commands off of the vendor website. Once it’s all set up, it does work pretty smoothly. But…come on!

In contrast, take a look at the [Snap Store.](https://snapcraft.io/store)

There are some technical differences between running a program from a snap, running it from a container, and installing it on your host machine directly.

Snaps are like containers because they:

- run on most Linux distributions

- include all their own dependencies and configuration

- only expose what you explicitly allow ( [I need to research this further!](https://ubuntu.com/core/docs/security-and-sandboxing))

- provide content to the user from the developer, without a packaging organization intermediary


Snaps are like native package-managed programs from a .deb or .rpm because they:

- appear as part of the local system, rather than a little mini VM with its own IP

- they extend the host system, rather than providing a single process

- cleverly share or de-duplicate the immutable base elements of these apps


[Canonical appears to be heavily emphasizing this](https://ubuntu.com/core) context, not just for us happy developers who like Ubuntu—but for the “edge” devices, the robots, network switches, appliances.

If I understand correctly, this is the niche that snap is going for. Make Linux software very portable—not by recompiling, but by breaking down a Linux application into large useful chunks which can be easily updated. This attempts to solve the same packaging and versioning problems Golang and Rust tackle by statically compiling their products. (see [Packaging Kubernetes for Debian](https://lwn.net/Articles/835599/))

