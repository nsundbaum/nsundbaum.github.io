---
layout: post
title:  "It's a marathon, not a sprint"
date:   2021-03-21 10:00:00 +0100
---

Speed is a key feature of successful development teams and organizations. As software developers, it is our job to turn abstract visions and ideas into something that users can touch, feel and use, the faster the better.

The faster we can go from idea to working software, the faster we can earn revenue on those ideas and the faster we can gather feedback from actual users to use as input to feed the next set of ideas (or refinements of existing ideas) to implement. Speed also allows us to react rapidly to opportunities and threats in our organization’s surrounding environment, such as those coming from competition, regulations, customers and market trends. Additionally, speed means that we can address internal issues such as bugs and other problems in our systems in a timely manner.

Ok, so faster is better. Got it.

Well, not so, hmm... fast. When it comes to software development, there is another force coming into play as well. Being fast over a week or two, or maybe even a couple of months, is of relatively little use to our business if we can’t sustain that pace in the long run. Very few companies build their success based on just a few weeks of produced output. Therefore, the speed we are talking about here needs to be of the kind that we as a team can maintain over a long period of time. To use a running analogy, we are participating in an ultra-marathon race, not a 100 meter sprint. And, just as running as fast as you possibly can for the first kilometer of an ultra-marathon will likely exhaust you and have a negative impact on your overall race time, optimizing for short-term speed in software development will actually make you slower in the long run and put your business at risk of being outperformed by competitors using a strategy more suited to the distance.

This means we need to balance short-term speed against long-term and in most cases optimize for speed of the sustainable, long-term, kind. So while there certainly are cases when crunching or taking on technical debt in the name of short-term speed is warranted, for example to meet a critical deadline, that should be the exception and not the rule.

Let’s take an example. As a developer, the faster you can crunch out a piece of code, the faster you can get the feature that you are working on into the hands of your users. Which hopefully translates into more revenue for your business. All good so far. But when optimizing for pure short-term speed, you probably didn’t have time to think about how your change impacts the overall architecture or write those automated tests. Perhaps you took some shortcuts, ignoring quite a few ugly parts in the implementation or maybe did some quick copy-paste from other places around the code base since you didn’t feel you had the time to extract those common utility methods. This is short-term speed in its essence.

The paradox here is that by cranking out the implementation as quickly as you possible could, you actually made yourself (as well as your team and your organization) slower in the future. Why is that? This added "slowness" comes from two main sources. First, taking shortcuts when implementing a feature usually leads to more problems and bugs connected to that feature. This means that developers need to spend more time fixing bugs instead of adding value to the product. Most of the time, bugs and other issues also means that developers have to context switch to a much larger degree, which in turn kills productivity, adding to the slowness even further.

Secondly, the next time you need to make a change in that specific area, this will be harder and take more time due to the shortcuts taken the first time. In this case, you can either chose to clean up the mess introduce by the original quick n' dirty solution or to shoehorn the change into the existing structure. Choosing the first option will take more time right now, but increase your long-term speed going forward. Going for the latter will obviously decrease your future speed even further, often creating a vicious circle.     

To summarize, in order to achieve sustainable speed we need to focus on quality, which makes the process of writing that piece of code in the first place a bit slower. However, that lost time is made up for by being able to maintain a higher speed in the long run. So if we aim to optimze our speed over months or even years, which is the relevant timeframe for most companies, this is clearly a winning strategy.

So, what are the enablers for sustainable speed? That's probably a topic for another blog post, but at a high level, it is pretty much all of those best practices in software development that are all too often ignored for the sake of short-term speed:

- Test automation and testing tools
- Spending time on design and architecture
- Paying off technical debt
- Continuous refactoring and improvement
- Code quality
- Process automation
- Documentation
- Communication

In closing, it is worth mentioning that the line between short and long-term is not always that clear-cut and that it is all too easy to get stuck in the wrong quadrant of the urgent vs. important matrix in our day-to-day work. When this happens, it helps tremendously to establish a long-term vision for which type of development organization to build and which practices, values and principles to follow based on that. In doing that, we can easily sanity check whether we are on the right track towards our vision, even though we of course sometimes need to make a few 100 meter sprints in the name of pragmatism to meet that critical deadline.
