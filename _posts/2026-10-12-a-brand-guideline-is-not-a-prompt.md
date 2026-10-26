---
layout: post
title: A brand guideline is not a prompt
description: Pasting the brand book into a system prompt is hope, not compliance. Brand rules belong in a graph, checked outside the model that writes the content.
---

Every on-brand generation demo I've seen does the same thing. It pastes the brand book into the system prompt and hopes.

It works in the demo. The tone is right, the copy sounds plausible, and nobody checks the rule buried at the back about trademark symbols. Then it goes into production and you find out what a brand guideline actually is.

A brand guideline is not a prompt. It's a set of rules with scope and exceptions. The logo needs clear space, except in this partner lockup. This product name is always capitalized, except in legal copy where it carries a trademark symbol. Never use this phrase in financial services. Those are conditionals that depend on channel, region, product and audience, and they interact. A paragraph of instructions in a context window doesn't represent any of that. It just puts the words near the model.

I was one of the founding engineers on Adobe GenStudio, and the decision that mattered most was treating guidelines as data. We represented a company's brand guidelines as a knowledge graph, grounded generation in it, and then checked the output against the rules separately from the model that wrote it. That separation is the whole point. The generator can be any model you like. The checker doesn't care. When an asset fails, a human reviewer sees which rule failed and why, instead of a vague sense that it feels off.

That's what let us ship a fully AI-generated marketing campaign and cut content production cycle time. A longer prompt would not have gotten there.

Prompts fail here for boring reasons. They don't compose: two sets of guidelines pasted together are a mess, and a sub-brand override is just more text arguing with other text. They don't version: you can't usefully diff what the model was told last month against what it's told today. They can't be audited: when legal asks why an ad shipped with a banned claim, "the prompt said not to" isn't an answer. And the model's compliance is a probability, not a property. Mostly compliant means you are shipping violations. You just don't know which ones.

Same view I have on harnesses. Keep the rules outside the model, where you can inspect them, test them, and keep them when the model changes. The model should be the easiest part to swap.

A brand book in a prompt is a suggestion, and a brand book in a graph is a contract.
