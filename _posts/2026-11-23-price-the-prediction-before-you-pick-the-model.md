---
layout: post
title: Price the prediction before you pick the model
date: 2026-11-23
homepage_summary: Decide what each prediction can cost before choosing between a frontier LLM, a gradient-boosted tree, or a shared domain model.
description: Think of a churn score as a System 1 token. Decide what each one can cost before choosing between a frontier LLM, a gradient-boosted tree, or a domain foundation model.
---

Most model choices I see are made backwards. Teams pick the model first and find out what a prediction costs later.

Start with the output instead. A churn score, an intent flag, a suppression decision, a routing label. Think of each as a System 1 token: fast, automatic, produced millions of times a day. Before writing model code, estimate how many of those a product needs and what each one can cost while the business still makes money. That number decides more than any benchmark.

There are three ways to produce them. Each one trades off talent, time, compute, and how fast the business underneath is changing.

A frontier LLM behind an API needs almost no ML talent and no upfront infrastructure. You can wire an agent to it and learn in a week whether customers care. That is exactly what it's for while the business is still moving. The trap is keeping it as the scoring engine. Agent loops multiply calls per entity, and at a hundred million predictions a day you are paying System 2 prices for System 1 answers. The margin goes first.

A gradient-boosted tree is the cheapest prediction there is, and coding agents now write the feature code and glue in an afternoon. But agents make code cheap, not data contracts. Every new tree brings its own feature table, training schedule and drift. Pivot the roadmap twice and you own a graveyard of pipelines nobody wants to touch, even if no person wrote them.

A domain foundation model costs the most up front: people who can pretrain, months of work, real compute. It pays off when the entities underneath are stable (users, devices, places, transactions) even if the products on top keep changing. You train the backbone once and run one daily inference job. After that, a new product is a thin head on existing representations, so one shared forward pass pays for every prediction you ship.

Agentic development doesn't remove the need for cheap predictions. It sharpens the split. Use the frontier model for low-volume reasoning and for discovery while the business is still shifting. Keep trees for the handful of high-value targets that won't move. Build the shared model once your products and agents need hundreds of different predictions over the same entities every day.

Price the prediction first, or the infrastructure will set the price for you.
