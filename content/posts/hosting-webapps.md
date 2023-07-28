---
title: "Hosting Webapps, Part One"
substitle: "Where to put my stuff"
date: 2023-07-28T06:26:28-10:00
draft: false
---
![](/img/infra-barbie.png "Even Geek Barbie says, Infrastructure is difficult!") 

Hard-working developers the world over are begging to not have to deal with infrastructure. Thus are born ["DevOps Engineers"](/posts/devops-and-job-titles/), a title which misses the point of breaking down the silos between development and operations. 

But that doesn't change the complexity of modern infrastructure. Does every developer have to understand how the product's CI/CD works, monitor production performance, set up the load balancers? Especially on a small or one-person team?

Hence the many attempts to simplify infrastructure and get over the hump between "it works on my machine!" and a resilient cloud deployment.

Let's talk about some approaches to solving this problem.

1. Static Sites (keep it simple!)
2. Cloud Hosting (learn to cloud!)
3. Platform-as-a-Service choices (out-source the hard stuff)

## Tammy, stand by the JAMs

Static sites came back into favor from a desire to cut through complexity. Remember when we just typed up some HTML, added some image links, and called it content? No need for a server running a CGI process or a database. Just update some content, publish, and off we go.

Static Site Generators like [Jekyll](https://jekyllrb.com/) or [Hugo](https://gohugo.io/) (which powers this site as of this writing) also embrace templating, allowing content creators to work in something simpler than HTML, CSS, and JavaScript. [Markdown](https://www.markdownguide.org/) is just the beginning, although it could also be all you require. Let the generator and its themes manage the look and responsiveness and so on. Let it prerender your pages rather than having the server generate them for each hit. And put everything on the client side reduces calls to the network. Your users' phones are burly! Make them work!

The [Jamstack](https://jamstack.org) (JavaScript, APIs, and Markup) extends this idea to include headless CMSes to manage the content. Now we're back to hitting the network a lot, but we have a nice separation of concerns: changes to the front end can stay isolated from changes to the data and content. Decoupling your site like this makes hosting choices more flexible, as well.

So how do you host your static site? You could just drop the output onto a cloud storage service, like S3 or even something from Dropbox or Backblaze. Oh, maybe you want a CDN to make sure its fast the world over? Maybe [Github Pages](https://pages.github.com/) or [Netlify](https://www.netlify.com/jamstack/) would handle that for you.

It's easy to go from markdown content to a generated static site. There are a few more steps involved in getting your static content hosted and behind a domain name, but those are well-documented. **A static site is a great choice if you want a website to be about the content rather than how it's programmed or the infrastructure supporting it.**

## Running your software on other people's computers

Maybe your project isn't just a website. Maybe you need to store data. Maybe you want to provide data, authenticate users, or allow users to control software beyond their own devices.

In that case,  you're probably going to want to run a database, and possibly an API of your own.

There are three main ways people do this with a cloud provider:

1. Run it on a virtual machine
2. Run it on a container service (Amazon ECS, Google Cloud Run)
3. Break it up into "serverless" functions

A more traditional deployment might work well on virtual machines if its pieces are tightly integrated and you pretty much know what kind of load it's expected to handle. On the other hand, deploying to VMs may mean you're dealing with shovelware, where your software lives on the cloud but gains few of the cloud's benefits. For example, you can pretty much only scale "up," redeploying on burlier systems with more CPU and RAM, etc. It may actually be more cost-efficient and easier to [colocate your servers](/posts/clexit/)!

![](https://storage.googleapis.com/gweb-cloudblog-publish/images/Artifact_Registry_54S8XHC.max-1500x1500.jpg "Google Cloud's pipeline")

More commonly, you'll want to [containerize your software](https://www.baeldung.com/cs/containers-vs-virtual-machines#container-basics). Containers let us work from standard templates--and manage that huge pain point in modern development, **environment and dependencies**. Moving your software into containers encourages and enables cloud-native benefits: **scalability**, **loose coupling**, and the **resilience** that comes with those two. Watch out that you don't achieve the worst of both worlds by splitting your services up but leaving them tightly dependent on each other. No one wants a "distributed monolith", combining the complexity of microservices with the fragility of a big does-everything program!

You can also totally design your API around serverless cloud functions, or Lambdas! Of course, these functions are running on servers somewhere, but as a developer you don't have to know anything about that. The upside is your code is broken out into pieces and possibly cheaper, as it's only run when needed. The downside is that the various functions need to communicate, be it through a database or a message queue. This may slow things down or just add more complexity.

Using containers (with Kubernetes or a more managed system like Google Cloud Run) or using serverless functions means **your app scales semi-automatically.** Yes, there's a lot to set up and tune. But it's manageable by a small team and very flexible.

## Build or Buy: Please just let me get back to writing my program

A static site can get you far! But when you need your own server-side functionality, the complexity increases dramatically.

Come back soon for Part Two, where we review some of the free and low-cost options that handle some of that complexity. We'll also delve into the liminal world of full-stack frameworks and Server-Side Rendering.