---
title: "The Complete Packaage"
subtitle: "Can people run what we've built?"
date: 2021-09-16T16:04:48-10:00
draft: false
tags: ["linux", "build and release"]
---
In the early days of Linux, by which I mean the early 90s, we built everything by hand! Small-batch, locally-sourced, artisanal .o files, linked using my grandmother’s secret ‘configure’ scripts and makefiles.

Today, we have perhaps even more software ecosystems to target, and we have many, many systems for managing our final product and its dependencies. It’s fascinating to watch the push and pull of conflicting technical goals.

## Birth of the Package Managers

So out of that primordial Ginnungagap of possibilities, came systems of packaging together pieces of software. Some of the goals of these packages:

- Everything in one place: binaries, libraries, configuration, docs.

- Dependencies: Split out common pieces. Your program uses the “ncurses” cursor library? So does nethack. It’s already installed. You want to install Jenkins? You’ll need a JVM to run it. We’ll automatically grab that for you.

- Versioning: This app works with this version of a library or part of the OS. Not with the older version, and not with the next major version. The package and database of dependencies keeps track of this for you.


Lots to manage, and much simpler to do so centrally. We can test the whole system at once. We can easily apply security updates. Thus was born longer-term support for Linux systems.

A big part of this policy involved splitting up pieces. Debian includes a minimal installation of Python, with many pieces separated into optional packages. This reduces bloat but can be inconvenient. What do we prioritize today? Do late 90s design decisions hold up today, or is the Internet so fast and storage so cheap that we don’t care as much any more?

## Other Kinds of Packaging

Package and dependencies management shows up in many other domains--sometimes painfully, sometimes productively.

- Node and JavaScript’s NPM: famously huge and famously ever-changing.

- Python’s pip: Python’s core library includes a lot, but pip helps you manage everything else, from manipulating MS Office docs to big data analysis tools.

- Windows-specific packaging such as NuGet, Scoop, and Choclaty

- Homebrew, expanding Unix tools on macOS

- iOS’s App Store and the various Android stores, one could argue

- Even Steam’s library of games fits our definition


Over time, we see an emphasis on making sure everything works smoothly--if everything is updated to the latest and (we hope) greatest. We have to consider our platform: is it a modern web browser? A JVM? Linux machines of a wide range of ages and versions?

## Bundle it All Together

Another push to simplify: including everything and sandboxing it apart from everything else. What started with full virtual machines has moved into containers, snaps and flatpaks.

Each of these projects attempts to provide each our programs an isolated world unto itself. I ask myself when doing this, am I making things simpler or more complex?

## Today: Vendor Static Binaries Winning?

Kubernetes, the container orchestration system and hottest thing nobody fully understands, is written in Go. Go takes the interesting default of statically linking its binaries. Instead of depending on a system of shared libraries, it just packs everything into each of its programs. That makes the result large but self-contained.

This methodology runs athwart policies like Debian’s; they want to break things up into pieces for finer-grained control.

[The debate on how best to package Kubernetes is worth reading about.](https://lwn.net/Articles/842319/)

Rust is another language which uses its own packaging system, cargo, to circumvent much traditional package management. Python developers, for example, have expressed tremendous relief that their Rust projects will grab their dependencies and run when deployed.

When we build something, we need to make that call--what will it run on? Today’s computers? Servers five years old? How can we simplify deployment and compatibility?

