---
layout: post
title: "Github Codespaces"
date: 2024-01-01 16:16:28 +0000
permalink: /2024/01/01/github-codespaces/
author: "sven"
---

Many production and supply chains have some form of retooling cost. Software is similar. It takes times to set up a development environment, ensure consistency and remind oneself of the work context.



A few years ago, I spent most days writing code in one form or another for broadly related projected. More recently, it's become an occasional foray, and quite scattered, so retooling has been more of a concern. The overhead of setting up my workspace, just to get a potentially small change made, is more significant.



Various options, contributions and ways of working have emerged over the years. From synced profiles, config inside projects and easier setups. Containerisation lends itself well to the development space, as do virtual environments, virtual machines, and so on.



[Github Codespaces](https://github.com/features/codespaces) is an interesting and potent take on this. It effectively bundles the editor, working space, source control and developer testing. Of course, as part of Github, it also brings closer the wider sphere of testing and deployment.



I'm now revisiting my ways of working to make the most of Github Codespaces, pushing myself towards one-click editing, simplified self-test and deployment. Crucially, it means that the wider dev environment is fully configurable and cloud-based, so I don't need to have a desktop set up with all the requisite tools - *a browser is enough*.



It's also giving new life to old kit. I'm using older devices that would ordinarily have been sent for recycling. Equally, the pressure is off to invest in something new.



A quick rattle through some other benefits:



* Codespaces can be ephemeral, and I've specifically reduced their lifespan. This encourages regular commits, and thinking about clean deployments more routinely.  
* The entire dev environment is configured inside the repository in Github, so I know every contributor has a like-for-like place to work. That reduces errors.



Security is a potential winner, in various ways, but as usual there are pros, cons and professional factors to consider that are worth exploring separately.



Ultimately, it means I can pick up a project, make a needed change, and create a commit in a significantly faster way.
