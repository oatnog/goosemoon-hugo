---
title: "Simple JavaScript Builds with Vite"
subtitle: "Next you'll be telling me I need a build system to publish HTML"
date: 2021-09-21T16:04:48-10:00
draft: false
---
When I talk with people who have been doing web development for a while, they always seem to complain about contemporary tooling.

## Modern Life = Unnecessary Complications

The way they tell it, if we want to use one library, let alone a framework, it always brings along seven more dependencies. They constantly morph and squirm underneath our program’s surface, like the bugs that make up the Oogie-Boogie Man.

And this is where we encounter the various efforts at “building” JavaScript programs. We need to…

- Make sure everything is included, and all the extras your new addition rely upon are also included.

- But it has to be compatible! So run it through a system that dumbs the code down for older browsers, including outdated efforts at adding modules to JS.

- But it has to be slim! So minimize it into a weird garbled JS blob.

- And prune the stuff you included but never used! “Tree-shaking.” A real term.


I’m no expert at JavaScript development, so I’m sure I’m missing more essential elements. (This blog is sort of a journal of my own learning, and attempts to start conversations.) But these are some of the considerations in going from your code to deployment.

## No, I Really Do Need This

Once you step outside your own pure vanilla JavaScript world, you find yourself juggling all of these requirements. And The Churn aside, may I suggest that people don’t write JavaScript because Vanilla JavaScript is a wonderful language. They write JavaScript because of the platform (our beautiful browsers) and libraries and environments that have grown up around that platform.

So we have more tooling. Traditionally, webpack. And that seems to work fine. A good build system keeps track of things, keeps their changes stable, and abstracts away some of the management a programmer does not want to think about.

And we deserve good tooling. Because the endless pieces and options and paths really do increase the barrier of entry, and I dream of a world where people can fire up their browsers and write real code. The first computer I got my hands on was an Apple ][+, and anyone could start it and type in AppleSoft BASIC to make real programs. That’s what I feel we could have, with all these JavaScript engines humming away. I want that first sit-down to code to be easy.

## Enter Vite

[Vite](https://vitejs.dev), which rhymes with yeet, helps clear away some of the extra lifting. And it’s small and quick.

If I were deeply invested in previous tooling, perhaps I would stick with webpack or its cousins. But Vite has been a pleasure to use, so I’m sticking with it. Vite includes setup templates for React, Vue, Svelte, plain JavaScript, Typescript, more.

Sometimes you like a tool because it does the thing you need to get done. Nothing else works quite correctly. So your tool, gawky and uncomfortable it may be, still becomes beloved.

Sometimes the fondness comes from how easy something fits into your workflow. You aren’t constantly adjusting or switching contexts; you just work. The tool gets out of your way.

## Live Updates: Hot Reload

When using a framework with Python, I got used to having what was in my browser update when I changed my code. I’d type something as simple as

```bash
$ flask run
* Running on http://127.0.0.1:5000/
```

Done. (And in debug mode, it provides an in-browser debugger. Python is pretty neat!)

This is feature long since embraced in the web dev front end world. I wish I could remember exactly when I first saw it—a demo of Ember? Meteor? A moment of silence, please, for those JavaScript frameworks who have gone before.

Anyhow, it’s a wonderful quality of life feature. I was “well chuffed” when I encountered it in the old Vue CLI, and even more when it zipped along with Vite. And just as easily:

```bash
$ npm run dev
```

No one should have to refresh their browser every time they make a change to their code—even if they are working in simple vanilla JavaScript.

And a final produce, suitable for serving statically or running from a Node server, is as easy as

```bash
vite build
```

## Just a Taste

There is a lot more to Vite, and to the choices one may make creating a web app. It seems to have set out to simplify development (less waiting, fewer reloads). But in the process, it also seems to provide Build People with a simple tool that just gets out of the way.

