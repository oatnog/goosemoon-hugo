---
title: "I Just Want to Run the Program"
subtitle: "Packaging a Desktop App for Linux"
date: 2021-10-25T16:04:48-10:00
draft: false
tags: ["linux", "build and release"]
---
## Packaging a Desktop App for Linux

Let’s say I want to run [Inky](https://github.com/inkle/inky), the editor and testing program for Inkle’s [Ink “narrative scripting language for games.”](https://www.inklestudios.com/ink/)

[Ink](https://www.youtube.com/watch?v=KYBf6Ko1I2k) lets me write choice-based narratives and embed them in the web, in Unity games, or wherever. It’s open source and real-life proven: the folks who created it use it to make amazing games such as [80 Days](https://www.inklestudios.com/80days/), [Heaven’s Vault](https://www.inklestudios.com/heavensvault/), and [Overboard!](https://www.inklestudios.com/overboard/) Lots of [other game developers use it too](https://www.mcvuk.com/development-news/want-your-story-to-drive-your-game-rather-than-vice-versa-inkle-and-failbetter-discuss-the-storytelling-potential-of-the-open-source-ink/), since it lets authors focus on the text while also managing branching narrative, state (the player character’s experiences and ongoing relationships with game places and with other characters) and substituting variable pieces of text. Some developers use it to prototype, while others build their game narratives around it.

Anyhow, say I just want to cook up and test some choice-based narratives? I might want to use Inky.

![Inky](/img/using-inky.gif "From the Inky Github repository")

The developers make it pretty easy to get and run the latest version. Just go to [the project’s GitHub releases page](https://github.com/inkle/inky/releases), download and run it. Inky bundles up everything using [Electron](https://www.electronjs.org/), a wrapper that lets web apps run as native apps.

When I download and unzip the latest release for Windows or macOS, it works great. The Linux app, though, gives me this:

![](/img/cant-run-inky.png "Runs fine from the command line, though! No GUI for you, Linux Desktop User!")

And working from the GitHub releases means we have to update manually every release. Let’s look over some other options to provide access to Inky.

## Debian Package

Ink and Inky are open source. So they should be packaged up and go into the regular Debian and Ubuntu repositories, right?

Only problem is, Ink uses C# and .NET. We could get these tools from Microsoft, but that would mean we’d have to add their third-party repositories for both building the tools and for the dotnet runtime libraries. That’s not so bad—we lose the “trusted and tested with this release” value of working from only the official packages, but sometimes it’s nice to get software straight from the developer. But it certainly adds more of a burden on a user who just wants to run a program.

Or does it work with [Mono](https://packages.debian.org/bullseye/mono-complete)? Or has the open-source dotnet Core supplanted that? or are there licensing / politics issues? More research needed. Oh boy.

As usual with open source ecosystems, [there are solutions](https://github.com/qmfrederik/dotnet-packaging)! But it seems like it would be difficult to get Inky and the command line inklecate tool into an official repository, due to the complicated dependencies. So if we took this option, we’d have a standalone .deb archive, which we’d have to serve up from somewhere.

Unless I’ve missed some official guidance on packaging, this isn’t a great choice.

## Docker Image

Containers are supposed to be light, ephemeral, immutable, disposable. If you make a change to a containerized (contained?) app, you’re supposed to change the Infrastructure-as-Code (the Dockerfile or similar), and spawn a fresh container.

That doesn’t sound like how I use a desktop application, although as a G-Suite user, maybe I should get over myself. Let’s look at what it would take to get Inky delivered via Docker.

- Dependencies: [.NET Core LTS](https://hub.docker.com/_/microsoft-dotnet-runtime/) image

- A version of Node JS.

- The [electron-packager](https://github.com/electron/electron-packager) tool, to wrap the web app as a desktop app

- Environment variables and settings to let the containerized GUI app show up on the host system’s display. DISPLAY and Xauthority and so on. But what if I’m running Wayland? Oh, there’s probably an emulator.


For today, I’ll put off writing the Dockerfile or Packer template. But these are some of the considerations. In the end, a user can run Inky by pulling a container image and running the app within it. It’ll be updated as the maintainer updates the image.

Workable, self-contained, but a far cry from mainstream desktop app convenience.

## AppImage, Flatpak, or Snap

If we’re going to put all the dependencies together into a bundle, rather than integrate Inky into an official distribution, we should also look at the trio of handy application-focused tools that accomplish that. [AppImage](https://appimage.org/)? Added to the Inky build tools two years ago! But not as trendy, and missing the other two’s exposure via their “app stores”— [Flathub](https://flathub.org/home) and [Snapcraft](https://snapcraft.io/store).

![](/img/snap-store.png "I don’t mean to be a fussbudget, but this is more my idea of how to install desktop apps")

So convenient! Do I really need another vendor-specific self-updater? No. No, I do not.

If we build and publish a snap of Inky, it’s on the public store and easy to keep updated.

![](/img/twine-snap.png "Twine has one! Where is Inky’s?")

But again, this would require wrapping up all the same dependencies as using Docker or Packer. But it might be very easy to just lean on existing snaps for dependencies.

## Other considerations

Will this choice add complications to file access (in the name of security)?

How would this affect the workflow of game developers? Integration with other related tools?

Does simplifying the installation and update process of using Inky help users significantly? Or is does this solve a very minor problem?

The big question here is still—what’s the best way to use a desktop application on Linux? And it’s interesting to consider the various options and potential pitfalls.

