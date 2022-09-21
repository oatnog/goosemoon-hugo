---
title: "DevOps and Job Titles"
subtitle: "The long underground culture war between sysadmins and SWEs"
date: 2021-09-25T16:04:48-10:00
draft: false
tags: ["devops", "build and release"]
---
Let’s all say it together: “DevOps is a philosophy, not a title.”

This is a trendy statement! But that doesn’t keep the word “DevOps” out of a hojillion job search results. I even have “DevOps Engineer” on my resume, because my manager at the start-up suggested it, and we didn’t know any better.

![]( /img/ualsah-devops.png "From the brilliant Unix and Linux System Administration Handbook")

Defining DevOps is beyond the scope of today’s blog. But we know it evolved out of Agile’s short, iterative release cycles—a switch from the very siloed “waterfall” software development process. Waterfallin’s formal structure was meant to put a stop to feature creep and get stuff shipped, as in “we can’t change all the features now! that’s development work, and we’re in the test phase!” Agile tried to address that method’s most common problem: shipping what was technically asked for and specced out, but didn’t wind up being what was really needed. If clients always respond with “oh that’s great, but what we REALLY meant was this,” why not shorten that cycle and get to client rejection of hard work right away? Ask a graphic designer about this process.

But Agile software development’s quick pace would slide to a halt at production deployment time. Turns out, the folks putting together the infrastructure need time to plan and design and adjust to changes too! So we put together the Dev people with the Ops people, and realize that software is one larger integrated problem, rather than disconnected pieces.

Add monitoring, iterations to improve based on its feedback, automation, continuous integration and continuous delivery, testing—and we’re getting closer to DevOps.

## There is only Zuul

I read _The Phoenix Project_, and it turns out that it entertains in a “tales from the trenches” kind of way and also clearly models that Dev → Ops breakdown. Totally worth reading.

So how do we break down the silos and get people working on all the important pieces together?

My mate Gregor said, “DevOps is a great way of thinking of the new Agile world, but like Agile, too many companies say ‘now we have a DevOps team and we're doing things the right way,’ which is so wrong that they might not understand how fundamentally they got it wrong.” Did those companies just create another silo?

## Job Titles for the Unwary

With these issues in mind, I will attempt to clarify what’s meant by some of the job titles flying around in today’s job market.

**System Administrator:** What! No one uses this anymore. If you see this title, the company is hopelessly uncool. You may feel like a custodian, walking the halls of ancient server rooms.

**DevOps Engineer:** A Software Engineer who can install software with ‘apt-get’. Has a homelab. 10 years experiences with k8.

**Site Reliability Engineer:** A Sysadmin who only cares about reliability and uptime. Because no one else likes those things.

**DevOps Engineer:** Wait, no, a DevOps Engineer is a SWE who knows how to set up Jenkins and hack together knots of Groovy scripts.

**Cloud Engineer:** Someone who knows how to set up all the latest exotic special services from cloud providers, but can’t remember how to check their IP address from a command line.

**Infrastructure Engineer:** Has odd distaste for reinventing the wheel. Loves Rube Goldberg machines. May have been a Network Engineer whose job was “outsourced to the cloud”.

**DevSecNetMICookBotOps Pro:** The natural and inevitable evolution of ongoing best practices in SDLC acronyms and job titles.

**Release Engineer:** A Build Engineer who knows how to update the microservices and compile release notes. Moves through life according to release cadences, which may be authentic, half, plagal, or deceptive. May have secret desire to be a Project Manager.

**Build Engineer:** A Release Engineer who is more interested in automating flocks of build machines than what the product looks like when it’s installed. May know Perforce and be suspicious of Git.

**DevOps Engineer:** A sysadmin who is desperately learning how to code just enough to get by. Proud of their Dockerfiles.

## Good Thing That’s Cleared Up

We can only hope that this name churn has a good side—perhaps room to define our own roles? Is this late-stage capitalism, or an evolutionary bloom?

Kubernetes.

