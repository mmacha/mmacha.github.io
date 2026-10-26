---
layout: post
title: A model is not a bidder
description: Prediction and activation are different jobs. Keep the behavioral model's output a stable score and let bidders, DSPs and audience tools consume it.
---

Most ad-tech teams that build a good prediction model eventually try to make it bid, and that's where it stops being good.

Prediction and activation are different jobs. A behavioral model estimates what someone is likely to do next: visit a dealership this week, shop for a mattress, book a flight. A bidder answers a different question. What is that person worth to this advertiser, right now, in this auction, given the budget left today, the pacing plan, the floor price, and how the campaign will be measured? The first question is about people. The second is about money and time.

When teams collapse the two, they fail one of two ways. Either the model gets trained on campaign outcomes, so it learns whatever the last campaign rewarded and is useless for the next one (a model tuned to cheap clicks for one retailer tells you nothing about intent for another). Or the bidder is built without real behavioral signal, so it handles price and pacing beautifully against a crude guess about who it's bidding on. You end up with a model that is only as good as the last campaign, or a bidder that is blind.

The fix is to keep the boundary and make the model's output a stable, scored object. Visit likelihood, intent by category, a score per person per day. Stable means it means the same thing tomorrow as today, and the same thing to every system that reads it. Then let activation systems use it on their own terms. An audience platform turns it into segments. A DSP uses it for targeting. A bidder reads it as one input among many and owns the economics.

This sounds less ambitious than one end-to-end model wired into one auction, and it is. It's also better. Predictions computed offline on a daily cycle and activated through many surfaces get reused everywhere, get evaluated on their own, and lift every downstream system when they improve. A model fused to one auction gets one shot and one metric.

The interesting next step is pulling some of this toward online inference, so the score can react to what happened an hour ago instead of yesterday. That's where I think the real work is. But the move only makes sense if the boundary survives it. A faster model that has learned to bid is still a model that has learned to bid.

Let the model predict, and let the bidder decide.
