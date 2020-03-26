---
layout: post
title:  "Getting up to speed on a new technical platform as a manager"
date:   2019-12-01 14:31:21 +0100
---

When joining a company as a technical manager, one of the major challenges in front of you is to learn the details of the technical platform(s) that you are responsible for. You are most likely not coding any more, or at least not making any major contributions to the code base, and with your days filled with meetings and other management duties, it can be a real challenge to find the time to actually dig into the more technical parts in order to get the understanding needed to do a good job.  

Depending on your role, background and position on the company ladder, the actual level of technical detail that you need will vary a lot. So before you jump into things, spend some time analyzing what amount of technical understanding that you actually need to do your job well.

For example, do you need to understand all details in the code, is it enough to grasp the most critical parts or should you start to build your knowledge from the architectural level and upwards? As engineers, knowledge is our main currency and therefore our gut reaction is often to go deep and detailed. However, that’s not necessarily where you’ll spend the most part of your time as a leader. Also, think hard about what effort it will take to keep that understanding up to date over time and if that is a realistic effort to spend in the future.

Having been in this situation myself several times, here are a few things that worked well for me:

* Draw a system map of all components in the platform and make sure you have a good understanding of the purpose of each part and how they interact. Make sure to ask questions to clarify the history and reason behind the not so obvious pieces. Surprisingly often, this is not documented at all and creating such a document will provide value both to future team discussions and to quickly give newcomers a good mental picture of your platform.
* Produce technical documentation and presentations. This is likely something you will have to do as part of your role in any case and it is a great opportunity to get more familiar with the platform. Initially, you will need help from your senior engineers but eventually you’ll manage most of it yourself.
* Ask your engineers where their biggest pains are in the technical platform and make sure you understand not just what but also why. This will give you an understanding of how things are connected, especially the not so shiny parts. As an added benefit, you’ll get a nice backlog of technical debt to address. Also, as these will likely be areas where various issues will surface in the future, you will then be in a better position to understand (and explain) why those issues happened.
* Facilitate postmortems and retrospectives. Again, make sure you ask all the whys. Being the new guy or girl, it’s ok to ask lots of stupid questions, so make sure you'll take advantage of that privilege.
* Treat your team's code review process as an opportunity to read and review code. Initially, you will focus mostly on just understanding the code and give feedback around general coding practices, but quite soon you will be able to have input on the actual solution as well.
* While I think that you should mostly focus on leadership, I sometimes find it useful to take on some small development tasks, such as fixing a trivial bug or a small improvement outside of the iteration's critical path. It will force you to dig around in the code base and familiarize yourself with surrounding processes such as CI, tooling and build processes.
* Pair-program with the engineers in your team, both senior and junior. You probably will have to take more of a backseat role, but you can still learn a lot and it is a perfect opportunity to ask questions. And when doing this with more junior engineers, there is likely a ton of useful feedback you can give them right away around structure and clean code without even knowing the details of the code base.
