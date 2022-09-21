---
title: "Learning JavaScript Pt. 1"
date: 2021-07-13T10:20:09-10:00
draft: false
tags: ["javascript", "education"]
---

At the beginning of 2021, I decided to get serious about learning JavaScript.

JavaScript. The dorky little browser language people love to make fun of. The catchy tune folks keep bopping along to, even as they skip the avant-garde prog metal band with more technical proficiency and experimental boldness. The language that [kinda-sorta took over the world](https://www.tiobe.com/tiobe-index/javascript/).

Why JavaScript, though? Why, when Python does everything I could possible ever want?

Why learn a new programming language? Why learn *anything* new? Conventional wisdom holds [we develop new forms of expression as our own thinking evolves](https://www.freecodecamp.org/news/why-we-will-always-need-new-programming-languages-3415869ea37e/). So we find new ways to do things, even if we know and trust the old ways--and our minds stay fresh and flexible.

But learning blossoms best when we get dirt under our fingernails. A hands-on project motivates! We can go far with these gardening metaphors. Learning benefits from regular mulching.

First, I wanted to get out of my comfort zone. Second, I wanted to be able to build modern web apps.

## Introductions

My first memory of a computer is a mysterious monochrome terminal at a university. Some friends of my mom's were showing us around. The program said "Hello, Liz! Would you like me to count to ten?" When my mom typed "yes", the computer wrote out numbers, one on each line, ranging from 1 to 10.

Looking back at my 4-year-old self, that's when I was hooked.

I asked why it couldn't say MY name. Could it count to one hundred? Oh, sorry, I was told. It doesn't do that. 

I knew that someday, **I** would make it do that.

## Old Tricks

Self-assessment time. Taking stock. What programming languages have I tackled in the past? Walk with me. Remember your own journey.

1. **[Logo](https://www.calormen.com/jslogo/)**, on an Apple 2 and later a Mac. Made videos with fractals. Koch snowflake is peak Logo! This stuff came in handy years later, when I taught Python's turtle's module to 13-year-olds.
2. **BASIC** ([AppleSoft](https://www.calormen.com/jsbasic/) and Integer), on an Apple 2. A smidge of 6502 assembly. No ability to pass parameters or return values. Dang. And yet people did so much with it! Mad properties!
3. **C**. First in high school. Tentatively. On a borrowed Atari ST. But I kept the [K&R book](https://archive.org/details/cprogramminglang00bria) with me forever!
4. **Pascal**. At my sluggishly behind-the-times university. Good fundamentals, though. At that point, [Pascal's reign on MacOS](https://computerhistory.org/blog/adobe-photoshop-source-code/) was over. But it still ran happily on the VAX! What were they teaching us!?
5. **Motorola 68000 and Intel x86 assembly**, at university. I remember really liking it! Even though our actual results were forgetable, it was a thrill to see what was really going on with the machines. Now, if we'd been learning how to [code demos for Amigas...](https://aminet.net/package/demo/intro/Gemanix)
6. **C++**. Borland C++ on 15 3.5 inch floppy discs. The ideas of the language and object oriented design made tons of sense! But while I walked away knowing how to implement polymorphism and friend functions for a toy project, I had little sense of what to do with it all. What would these conceptual frameworks get me, in my programs? Maybe that would have come eventually. 
7. **Perl**. The Camel Book. "There's More Than One Way to Do It." Smug but memorable philosophy. It got me my first developer job. It's trendy to mock Perl now, but [Consider Phelbas](https://www.goodreads.com/quotes/753765-gentile-or-jew-o-you-who-turn-the-wheel-and). As DevOps has moved so much value into providing "glue" to join pieces together, maybe we should have a moment of respectful silence for our [first "glue" language](https://linuxgazette.net/issue64/okopnik.html).

8. **Tcl/Tk**. For 5 minutes. I gave a script a [GUI](https://www.tcl.tk/) so the shipping folks would use it! And ask me about c|net's '90s CMS and web template rendering system.
9. **bash shell scripting**. In the old days, that's how automated builds worked. The shell remains so [reliable, versatile, and sturdy](https://www.redhat.com/sysadmin/stupid-bash-tricks). 
10. **make**. Does make count?
11. **C++** a second time, working on [BeOS apps and utilities](https://www.oreilly.com/openbook/beosprog/book/ch03.pdf). Now it was practical!
12. **Python**. Oh. Wow, this was really it! I can't remember the first project where I used Python. Was it the bug tracker migration? Or the Django release-notes generator? Like so many people, I fell hard for Python. It felt so comfortable and fun. A language that gets out of your way.
14. **Groovy**. I didn't quite get the point, unless you were deep into the JVM. Still, it's really convenient and easy.
15. **Objective C**. Got a good handle on it in EdTech grad school. Just before Swift came out. Sigh.
16. Back to Python, Flask, etc. It remained my happy place, comfort zone, whatever.

Okay! So does this make me a "polyglot"? or just a dilettante? 

I think I've learned something interesting and limbering from each of these programming investigations. It's not a resume list of skills--it's layers of building blocks, an evolution of ideas and approaches. I got really comfortable and accomplished with a few of them. At some point, though, I realized I was probably lionizing Python and keeping myself from growing.

## So What Happens Now?

I spent a decade as a teacher, out of the computer biz. I was still keeping an eye on things, tinkering with the home lab, whipping up quick tools to help with student seating charts and other management tasks. But at some point, I realized I wouldn't be teaching forever. I sat down to catch up and git gud at computers.

But what to focus on? What would get me excited? What would get me employed back in the ole Tech Sector?

- I did some online courses and [got certified as a Linux sysadmin](https://goosemoon.org/post/lfcs/). I've been using Linux on the server and occasionally desktop for decades. So it was fun to check in, fill in gaps.
- I poked around with cloud concepts, comparing AWS, Google CP, and Azure. Compared more managed hosting choices like DigitalOcean and Render.com. Wrote some Dockerfiles. Spent some time grappling with Kubernetes and its implications. Lots more to investigate here!
- I went a bit deeper into Python. Books and tutorials, promising "go from intermediate to advanced!" I know and appreciate the ecosystem a bit more. Massaged some data with Pandas. Put it up as an API.
- I thought about Go. It seems pretty perfect for me. C-like, trim, spry, but without memory management traps. Java's promise without all the heaviness. Rust looks neat, too. But I have not yet gotten moving with either. 
- Then I finally found myself looking back at JavaScript and yer modern webapps.

## Wait, Didn't We Say JavaScript Was For Millenials?

Kids and their newfangled ideas of what goes on a server!

And invading the backend isn't the worst of it. I sat with some web apps, and realized that my Flask-templated little websites really, really looked their age. It was like there was a whole platform out there I was ignoring. I mean, I was an Amiga user. I'd ignored popular platforms before.

But maybe that just meant that it was time for me to dig in and understand something that's new to me.

### Check back next time for [Part 2: Vue and that Asynching Feeling](/post/learning-javascript-ii/)

