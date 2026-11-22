---
layout: post
title: The harness is a mold, not a product
homepage_summary: Keep cognitive scaffolding replaceable, keep system boundaries hard, and use verified traces to train smaller models when volume justifies it.
description: The wrapper around the model matters more than people admit, and it still keeps getting thrown away. Both are true, and the resolution is a mold.
---

The harness crowd has one true thing and one dumb thing.

The true thing: the wrapper matters more than people want to admit. Take one model, put it in five different harnesses, and the spread is bigger than the spread between the models themselves. Rankings flip. The person who writes the loop decides more than the lab that trained the weights, which is uncomfortable if you spent $10B on the weights.

The dumb thing is concluding that you should build a thick harness and sell it as a moat. That confuses two different layers. Typed tool schemas, sandboxes, permission gates, and deterministic validators are permanent system boundaries. You keep those no matter how smart the weights get. Cognitive scaffolding is the opposite: context resets, multi-agent planners, reviewer loops, and the 40 tools that should have been 2. Every piece of cognitive scaffolding is a workaround for something the model cannot do this month. Next month it can, and now your clever workaround is making it worse and you do not know because you never wrote an eval. Look at Anthropic, OpenAI, and Cursor. They delete their own scaffolding constantly. Most harnesses in the wild have no evals. The whole field agreed the harness matters and then did not bother measuring it.

So what is the cognitive scaffolding for if it keeps getting thrown away? It is a mold. You run the expensive model inside it, filter its output through your evals, and keep the verified traces shaped like your problem. Unverified logs just distill retries and silent constraint drops. When volume, latency, or margin finally justifies owning the weights over calling a cheaper API, those verified traces become the training set for a smaller model, provided you handle the distribution shift once the retry loops come off. Then you take the mold off. Nobody frames the mold.

This is also why LangChain-style frameworks never worked (the abstractions fight the model, and the model wins). And it is why the "we have a proprietary harness" pitch deck should make you nervous. They have cognitive scaffolding. The building is the evals, the deterministic boundaries, and the verified traces, and they usually do not have those.

Keep your system boundaries hard, make the model easy to swap until volume justifies distilling it, and keep the mold out of the cap table.
