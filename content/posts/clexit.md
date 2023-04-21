---
title: "Cloud Exit!"
subtitle: "When does it make sense to just run your own machines?"
date: 2023-04-17T16:04:00-10:00
draft: false
tags: ["linux", "cloud"]
---
## Startup Dreams: Oh, The Scaling You'll Do

Every startup wants the problems that the cloud promises to solve.

Every startup wants to have a breakthrough moment of intense popularity--what we used to call getting "Slashdotted", which meant being linked to in an article on that old site people read before Hacker News or Reddit. Unexpected traffic used to mean the site went down. All you'd see is a MySQL error, complaining that it couldn't find its socks.

[System Design](https://blog.bytebytego.com/), load balancing, [static site generators](https://jamstack.org/), edge computing...there have been many efforts to keep sites running and speedy under unpredictable traffic. But one could argue that this problem (that everyone wants to have) was a prime force that moved software to virtualization, cloud VMs, containers, and orchestration.

Too much load? Just spin up another copy of your server! That has it own problems, of course, like configuration management, keeping your databases in sync, automation.

But over time, the cloud became not just a scaling tool. Its allure came from massive convenience--the path of least resistance for developers. Write a web app. Push it live. Updated it just as quickly!

(And of course, this lead to a mess of bespoke deployments, creating jobs for [Platform Engineers](https://circleci.com/blog/what-is-platform-engineering/) who hope to keep things standardized and reduce friction.)

## A Thousand Tiny Startups

This convenience--from concept to deployment to ongoing continuous delivery--has affected the software development landscape more than promises of more scalable, simpler ops. It's similar to the "hobbyist" free plans so many SaaS tools use to get you through the front door. You can operate just fine, abstracting away complexity, while you have no customers! And all we hungry developers have to do is keep an eye on our cloud costs and try not to go too far over the limit.

Is it the most cost-efficient way to run a startup? What are the trade offs? and when do you start dedicating people to watching your cloud costs?

But for some startups, the attitude becomes--who cares! Get that minimum viable product out there and ride the wave! Maybe you'll have unpredictable or just irregular service needs. Or maybe you'll explode and have to grow very fast.
The cloud vendors tell the story that they'll be there, making growth easy and sustainable during the transition to mid-sized and large business (or acquisition).

And the cloud vendors want to be one-stop-shops, encouraging you to stay in their ecosystem as you add more pieces (databases, storage, API endpoints, etc). Sometimes this works fine: your site's usage grows, so you start caring more about analytics, so you start using your platform's add-on. Sometimes this leads to a mishmash of redundant services and develop confusion. But people grow attached to the tools they know.

So small software shops become convinced they need the cloud. We need it to get successful quickly, to avoid being Slashdotted, and to keep growing when we get profitable. Or so the story goes.

## Please Use My Cloud App

Another side to the story: managing customer support. You see non-tech businesses who have been hosting a tool (say, document management) on their own servers in their own offices. Maybe they have liability requirements. Maybe they want the perceived reliability of regional access and they are in a distant region (Hawaii, for example).

Suddenly, their vendor is talking up the benefits of moving everything to their cloud product. No more local maintenance and upgrades! And let us manage your client software, too! Going from native to web means never having to ask before updating out from under users. Heh heh.

Such a business finds itself asking, who is reaping these benefits?

And the software vendor is thinking in terms of cloud services now, too, so they find it harder and harder to keep supporting local installations. 

For some products, this may make sense. But it's not so universal. If you're using an issue tracker and planner like [Jira](https://news.ycombinator.com/item?id=25594451), do you want to just host it yourself, or pay a fee and hope your experience and performance is a priority?

As always, there are trade-offs. But don't forget to follow the money. Cloud vendors dream of big companies with unpredictable computing needs, but they are happy to keep billing mid-sized businesses with very predictable needs.

## So What Were You Saying About A Cloud Exit?

People used to host their own servers. If we didn't want to be in charge of racking and running cables and being accessible in multiple regions, we'd co-locate the servers.

When does it become more cost-efficient to do that again, rather than renting out someone else's server?

Could this actually be more resilient than putting all your eggs in one cloud vendor's basket? (Cross-cloud seems like sacrificing all the promised simplicity, requiring even more experts to manage the variants.) What if AWS-East went down, but your app kept on chugging, happy in its little datacenter?

When is cloud hosting more trouble and expense than it's worth?

[David Heinemeier Hansson has been blogging about this process for months.](https://world.hey.com/dhh/why-we-re-leaving-the-cloud-654b47e0) His company, 37signals, ran the numbers and plan to save millions leaving the cloud in 2023.

[Freelancer Brian David Hall has pared down his "personal stack", replacing some cloud tools with local utilities and datastores.](https://briandavidhall.com/stack/). It looks like a more focused and fun workflow. Keep those backups fresh, Brian!

## Signs Point to Maybe

Is the cloud magic and the future of everything? Is running your own machine something only for neckbeard cranks on [/r/selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted)?

The cloud is amazing and has made so many new developments easier. But! Remember you're being sold a product. Were you promised a simple life from keeping your work on the cloud and using SaaS vendors for everything? Anyone who has tried knows that route has its own complexities.

As a SMB (Small or Medium-sized Business), judicious use of cloud resources can make your work much more flexible and allow you to respond quickly to change. That's very valuable.

Some things are best left to SaaS or the cloud. I wouldn't want to run my own email server, for example. But before you sign up for a Managed tool or just turn on that cloud vendor API, consider how much work and money it will really take. The age-old question of "build or buy" has startling relevance to infrastructure, despite conventional wisdom. You have the tools! Go use them to make something amazing!
