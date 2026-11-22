---
layout: post
title: "Where did the ML research go?"
date: 2026-11-17
homepage_summary: Training loops are becoming routine engineering; the real ML research moved into ungameable verifiers and reward integrity.
---

For a decade, machine learning scaled by driving the marginal cost of a training example toward zero. Scrape more text, log more clicks, ingest more passive exhaust. Recently, a friend who builds RL environments for frontier AI labs told me a single training task now costs $1,000 to $3,000, and he expects that price to climb as models get stronger.

In the same conversation, he noted that RL itself is starting to look like routine engineering. Package an environment in Docker, attach a reward function, run rollouts, and update weights. Those two observations sit in direct contradiction. If the training loop is commoditized infrastructure, why does one problem cost three thousand dollars?

The money does not pay for the algorithm or the containers. It pays for reward integrity. Once a policy is capable enough, it stops solving the spirit of a task and starts exploiting every crack in the evaluator. Authoring a stateful environment with deterministic verifiers and edge-case checks that a frontier model cannot game is slow, adversarial work. Every time the base model improves, existing evaluations collapse into shortcuts. The bottleneck is no longer generating rollouts; it is proving that a passing rollout actually solved the problem.

That cost structure exposes a split that most commentary misses. People argue that foundation models made traditional ML research obsolete, or conversely that every team building agents now has to solve continual RL. Neither holds up. Most applied agent teams call frozen APIs, iterate on harnesses, and ship retrieval. They are not updating weights. Only two groups face this research bottleneck at scale: frontier labs and vertical platforms with proprietary production feedback loops.

Frontier labs pay $3,000 per synthetic task because they do not own the downstream world. Applied platforms have the opposite problem. We already operate inside live environments with massive streams of real outcomes, but the rewards are sparse, delayed, and distorted by local incentives. Train a behavioral model on cheap clicks, and it learns to harvest clicks rather than predict real visits. Grade generated output with a loose prompt, and it learns to match the tone while dropping the hard constraint. In both settings, the failure mode is identical: a capable optimizer finding the cheapest path through a leaky reward.

ML research did not disappear when foundation models got good. It moved out of model architectures and into environments, verifiers, and feedback loops. Running the training loop is increasingly an engineering problem. Designing rewards that measure what you actually care about, and keeping them ungameable as the system adapts, is the research problem now.
