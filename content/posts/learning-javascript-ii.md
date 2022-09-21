---
title: "Learning Javascript Pt. 2"
date: 2021-07-25T15:18:44-10:00
draft: false
tags: ["javascript", "education"]
---
Last time, I enumerated all the dialects I've attempted in my life-long efforts to communicate with computers. I valiantly resisted drawing any sort of *family tree* of programming languages through the decades. It's diverting to develop taxonomies and tease out relationships and influences. I think this list points out just how much fun it is to build systems and tools with computers.

But what I wanted to emphasize was the task-oriented way someone can approach learning. Want to adapt something? Need a tool to get things from one place to another? Want to automate something for yourself or your team? Here's a way to tell the computer what you need.

And this is why so many people loved Perl, while it had its place in the sun. "There's More Than One Way To Do It" appealed to people who were intimidated by software design. Don't worry about algorithms, Perl seemed to say. You can be clever or simple, as you like. Just make a go of it, and you'll probably find your way there! It's the [Unix Philosophy](http://www.catb.org/esr/writings/taoup/html/ch01s06.html) in practice.

This liberal attitude is why Perl brought joy and fun to the world. For the (mostly) self-taught, like myself, it asked me to grab the "Swiss Army Chainsaw" and get to work. "Perl is a language for getting things done." "Perl is not a _tidy_ language."

This "shoot from the hip" attitude is also what drove people away from Perl. Try it! It'll definitely do something! But the thrill of hacking something together would fade when we looked at our scripts a few weeks later. What was this supposed to do? What was this little idiom that had seemed so clever? How had we managed to write something so incomprehensible? Perl got mocked for being a "write-only" language--you can write it in, but you sure can't read it. And that's not completely fair; I've read some very clear, well-organized, and straightforward Perl. And yet. And yet.

### Code Ninja vs. Code Monkey

How do software design patterns, good or harmful, establish themselves in general use? I'm not even talking about algorithms--not my area of expertise--but more about the ecosystems and conventions that grow up around languages and tools.

The mid-nineties saw Perl 5 (which among many things, added modules, which birthed [CPAN](https://web.archive.org/web/20001109034800/http://www.cpan.org/modules/00modlist.long.html#Part2-ThePerl5M) and its multitudes--remind anyone of today's JavaScript packages?)

At the same time, Sun produced version 1.0 of Java and the JVM. Java, now decried as verbose, full of boilerplate, and designed for tedious business logic. How uncool! But at the time, its standardized platform coupled with object-oriented structure did feel revolutionary. And I still feel the tension between Perl's "get stuff done" and Java's "please please let this be clearly defined and maintainable, even if it seems wordy right now". 

Brendan Eich, JavaScript's designer and first implementer, blogged in 2008: "The big debate inside Netscape therefore became 'why two languages? why not just Java?' The answer was that two languages were required to serve the two mostly-disjoint audiences in the programming ziggurat who most deserved dedicated programming languages: the component authors, who wrote in C++ or (we hoped) Java; and the 'scripters', amateur or pro, who would write code directly embedded in HTML."

So looking back at the beginning of 2021, I now realize I started my current attempt at JavaScript in the same way I'd decided to learn Perl in the '90s. Just pick up a thing and go! Project-driven learning. I wanted to find out if a "scripter" approach could scale with JavaScript, in this age of Node and massive web app frameworks.

### What Is This Fine Manual You Speak Of?

In the first bits of JavaScript I pushed to Github, in 2016, I am reminded of people suggesting I stick to JavaScript proper first. Stay away from all those opinionated libraries and frameworks! But that lasted about as far as my wanting to access the JSON info I was serving up with Python and Flask. [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest) just seemed so tedious next to jQuery's $.getJSON(). But either way, I was cargo-cult-coding. I didn't quite understand what I was doing.

Nonetheless, in 2021 I decided to ignore the wisdom of my elders and just start scavenging. What could I figure out from the Vue docs? What could I pick up from the [Chart.js](https://www.chartjs.org/) examples? Again, I muddled through some syntax, and sometimes things clicked (oh, you mean a map is just a kind of List Comprehension, which I love using in Python? No, Allan. Other way around. But now you know. Oh, those curly braces around your variable name just mean you unpack things? Just like Py--...) And others remained muddy but worked decently.

*Some of my biggest pain/aha points:*
- Not understanding npm and how many packages could get drawn into my dependencies as I experimented. (Allan, it's just like venv in PYTHON)
- [async/await](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await) whens and whats and please just load my JSON! That all makes sense now, though.
- Arrow Functions. Are they magic?
- Stepping into and out of various UI toolkits just for a simple slider. 
- mixins. How does this fit into the object model I learned with C++?
- Dates. And doing math with them.
- Vue3 vs Vue2 and incompatible libraries. Wait, this really is just like Python.

But in the end, I [made](https://github.com/oatnog/tih-frontend) a [thing](https://tih-frontend.onrender.com/). (Powered by [another thing](https://github.com/oatnog/tih-api-flask).)

*Stuff I had fun doing*
- This little Play/Pause button:
{{< gist oatnog acae12e98954bdc819a6017a7effe4bd >}}
- This adorable one-liner to check the environment for dev vs prod defaults:
{{< gist oatnog 853b5fd64005b625130a479ef0fdb449 >}}
- [Creating the API](https://github.com/oatnog/tih-api-flask) using Flask, Pandas, and feather. It's a lot of fun to take a bunch of data and expose the useful and clear bits! Okay, Allan. Get back to learning JavaScript!
- Just getting a handle on Vue and reactive properties. Maybe I'll try something else next time, but Vue was a good time.

### Next Steps
I liked making something! I enjoyed, to a point, discovering new syntax and structure behind every curtain. But I knew what I'd wound up with had its bright points and its, you know, messy points.

It was time to get more methodical. Maybe this was the time to get back to a thorough grounding in programming, not just the ad-hoc approach I'd championed for so long.

I picked up [Eloquent JavaScript](https://eloquentjavascript.net/). I like the writing style, and I appreciate that it's trying to remind me of how to program, not just how to JavaScript.

I started [freeCodeCamp](https://www.freecodecamp.org/)'s JavaScript certification. 300 hours? Yeah, right. Let's breeze through this!

### Next time, see how Allan Schools Himself.


 


