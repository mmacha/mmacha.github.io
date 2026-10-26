---
layout: post
title: Your synthetic customer should have a past
description: Persona agents tell you what a described person would say. A behavioral model tells you what an observed person would do, and you can check it.
---

Ask an LLM to be a 34-year-old mom in Phoenix on a budget, then ask whether she'd switch to a new grocery delivery app. You get a thoughtful answer. Run it ten thousand times with different personas and it starts to look like market research.

It isn't. The agent has no memory of this woman, because she doesn't exist. What comes back is the model's sense of what people matching that description tend to say, averaged over everything it read. That's a prior, not a population.

The average is the problem. Give fifty agents the same persona and the answers bunch together. Fifty real people with that profile are all over the place, and the outliers are usually the customers you care about. The agent also has no idea how often people like her cancel after the first month unless you tell it, and then you're writing the answer into the prompt.

Persona agents do fine on attitudes, the kind of thing people say in a survey. But what people say and what they do have never lined up well, and revenue follows what they do.

So start from what they did. A behavioral model trains the way an LLM does, predicting the next token, except each token is an event: a purchase, a session, a search, a cancellation, with its timing. In that setup a profile isn't a description. It's someone's history. To simulate her, feed the history in and sample forward one event at a time, and thirty days of rollout follows from what she has actually been doing. What-if questions work by changing the world and rolling out again: introduce the new price tier, compare to baseline.

The limit should be said out loud. When the change resembles things the model has seen, this works. When it doesn't, the model still answers, with the same confidence. Check counterfactuals against real holdouts before anyone acts on them.

Here's the part I actually care about. Nobody can tell you a persona agent's answer was wrong. A rollout has a real answer waiting a few weeks later. Hold out the most recent month, simulate it, compare. Did the model rank the products each person actually bought? Does each product's share of simulated purchases match reality? Do purchase frequency and time between sessions keep their real shape? When those numbers slip you find out before a customer does.

The LLM still has a job: take a plain-English question, turn it into a change you can simulate, and write up what came back, with every number tracing to a rollout. It frames and explains. It doesn't generate the behavior.

Personas are still the right tool when there's no behavior to learn from: a category that doesn't exist yet, or a why question instead of a what question. Label the output as hypothesis and move on.

Most synthetic-user products today are persona agents underneath. Before trusting one, ask the vendor how you'd find out if it's wrong. If the answer doesn't involve comparing output to real behavior, you're buying a story.
