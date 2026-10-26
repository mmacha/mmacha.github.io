---
layout: post
title: An audience is not a model
description: Ad-tech trains a model per audience. The audience should be a readable query over one behavioral model's predictions, not a model of its own.
---

Ad-tech has one unit of work, and it picked the wrong one.

Ask most data teams how they build an audience and the answer is a project. Someone wants people likely to buy a car soon. A data scientist pulls a seed list, trains a lookalike model, builds a pipeline to score it, and schedules a refresh. Then someone wants luxury car intenders who also shop at outdoor stores, and the whole thing happens again. Every audience is its own model, its own pipeline, its own way to fail.

That's backwards. An audience is not a model. It's a query over a model's predictions.

The thing you should train once is a behavioral foundation model. Feed it what people actually do, physically and digitally (where they go, what they do online), and have it predict likelihood across thousands of categories at once. Refresh it daily. Then an audience is a definition you write on top: high likelihood here, low there, active in this region. It's a filter, and you can read it.

Once you flip it, a lot gets easier. A new audience costs a query, not a sprint. Definitions become checkable, because you can look at one and see exactly what it selects and why. Two audiences can be compared line by line instead of by squinting at overlap reports. And when the model gets better, every audience built on it gets better the same night, not just the one somebody remembered to retrain.

It also changes what you can hand to a non-expert. We built Audience Builder, an agent that takes a plain-English request and writes the audience definition. That only works because the definition is a readable object. You can't ask an agent to explain a lookalike model's weights to a media buyer. You can ask it to explain a filter, and the buyer can push back on it.

The per-audience lookalike is the anti-pattern hiding in plain sight. Nobody can explain why a given person is in it. Nobody can tell you how it differs from the lookalike someone trained last quarter for a similar brief. It drifts quietly, and when it stops working the only fix is to train another one. A shop with hundreds of these doesn't have a modeling capability. It has hundreds of small, unrelated guesses.

Train the model once, and make the audience something a person can read.
