---
layout: post
title: "Where did the ML research go?"
date: 2026-11-17
---

I was talking to a friend who builds RL environments for frontier AI labs. He mentioned that a single training task can cost $1,000–$3,000, and he expects that number to go up as models get better. I found that surprising. We've spent years making training data cheaper, and now apparently a single problem can be worth thousands of dollars.

He also mentioned something interesting. With how capable foundation models have become, a lot of RL is starting to look like an engineering problem. Package an environment in Docker, define a reward, run rollouts, and train.

That got me thinking about something else. There's been a lot of discussion about how foundation models have made traditional ML research less relevant. Why train a specialized model when a general-purpose one can already do the job?

But I wonder if we're missing the other side of this. RL, online learning, continual adaptation, curriculum design. None of these are new ideas. But until recently, relatively few companies had the models, infrastructure, or economic incentive to work on them at scale. Now everyone building capable agents has to think about them.

And the problems are far from solved. How do you find tasks that challenge an increasingly capable model? How do you know it learned something rather than just gaming the reward? How does a deployed model keep learning without forgetting what it already knows?

Maybe foundation models haven't reduced the amount of interesting ML research as much as they've changed where it happens. I find that quite encouraging. The models are getting better, but figuring out how they should learn from experience still seems wide open.
