---
layout: post
title: The harness is a mold, not a product
description: The wrapper around the model matters more than people admit, and it still keeps getting thrown away. Both are true, and the resolution is a mold.
---

The harness crowd has one true thing and one dumb thing.

The true thing: the wrapper matters way more than people want to admit. Take one model, put it in five different harnesses, and the spread is bigger than the spread between the models themselves. Rankings flip. The guy who writes the loop decides more than the lab that trained the weights, which is uncomfortable if you spent $10B on the weights.

The dumb thing is the conclusion people draw from it, which is that you should build a thick harness and sell it as a moat. Go look at who actually builds good harnesses. Anthropic, OpenAI, Cursor. They delete their own stuff constantly. Every piece of scaffolding you add is a workaround for something the model can't do this month (context resets, planners, reviewer agents, the 40 tools that should have been 2). Next month it can, and now your clever workaround is making it worse and you don't know because you never wrote an eval. Most harnesses in the wild have no evals. The whole field agreed the harness matters and then didn't bother measuring it.

So what's the harness for if it keeps getting thrown away? It's a mold. You run the big expensive model inside it, you log everything it does, and the traces come out shaped like your problem. That's your training set for the small cheap model that replaces the big one. Then you take the mold off. Nobody frames the mold.

This is also why the LangChain-style frameworks never worked (the abstractions fight the model, and the model wins). And it's why the "we have a proprietary harness" pitch deck should make you nervous. They have scaffolding. The building is the evals and the traces, and they usually don't have those.

Build it so the model is the easiest thing to swap, swap it every time it's worth swapping, and keep the mold out of the cap table.
