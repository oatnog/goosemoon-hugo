---
title: "Continuous Integration Choices"
subtitle: "Wow, such Jenkins"
date: 2021-09-27T16:04:48-10:00
draft: false
---
In the olden days, we ran big builds that took hours. We ran them automatically, maybe twice a day, on all our target systems. They ground along, and we tried to figure out just how much of that time was ‘make’ opening and closing filehandles.

## By Definition, The Build is Never Broken

Around The Year 2000, though, a colleague blew my mind. He told me of how when he worked at [General Magic](https://en.wikipedia.org/wiki/General_Magic), part of every check-in/submit/commit to the main source trunk included a full clean build. If your change broke something, it didn’t go in until you fixed it. This was before distributed version control like Git had taken off, so we were very fixated on a central canonical repository of source code. It also foreshadowed the “test then promote” pipeline architecture.

## Integration, Continuously

Leaving aside continuous delivery for a moment, it took a while to get to continuous integration. If every time a change is made, we have feedback on how well it worked (from broke the build completely…to built, but screwed up the configuration and/or database…to running great but spits out mistakes), then we are a lot more Agile. Now we take it for granted that our changes will automatically be integrated with everyone else’s, and not just built but tested.

## CI Tools Overview

Any CI tool exists to facilitate a pipeline: a series by which changes get first built, next tested, and finally deployed. At every step, we get feedback. We monitor and log production changes, so we know when improvements or problems appear.

So with those goals in mind, I’m going to make a list of CI tools. We’ll likely go into each in more detail in future blogs.

- [Jenkins](https://www.jenkins.io/). Old, established, works with most things, possibly clunky, but it gets there. People ask, if I’m starting fresh, does it need to be with Jenkins? A lot of game studios seem to like it—building for various targets.

- [GitHub Actions](https://docs.github.com/en/actions). If your stuff is already on GitHub, instead of hosted locally, this seems to have a very good reputation for simplicity and efficacy.

- [Circle CI](https://circleci.com/). Popular. Sort of corporate?

- [Travis CI](https://www.travis-ci.com/). Free for open source projects, which worked for Perforce for a while.

- [Taskcluster](https://taskcluster.net/). Super powerful massive cloud build system. Mozilla’s baby.


Honorary mentions include [Gitlab](https://docs.gitlab.com/ee/ci/) (bonus points for hosting your own), [Buddy](https://buddy.works/), and [GoCD](https://www.gocd.org/).

The final question, of course, is what does your product look like? What kind of testing and validation does it require? Website, microservice, collection of interdependent services, mobile game, what?

Please let me know if you’re interested in any of these, or if I’ve missed your favorite.

