---
layout: post
title: "Messages are not locks"
date: 2026-11-27
homepage_summary: I was standing in front of the TV when a deploy I’d asked a worker to hold went out.
---

I was standing in front of the TV when a deploy I’d asked a worker to hold went out. The worker got my message. It just got to it after the deploy.

For two days I ran a group of coding agents from my phone to fix up my home server and TV. One session coordinated. Workers from Claude, Gemini, and Codex built things and reviewed each other’s code. The code was rarely the problem. One worker wrote a deploy script with a container ID and a set of file fingerprints baked in. An hour later another worker deployed something, the fingerprints changed, and the first script was useless.

Having a different model review the work was worth it. It caught a script that could print `PASS` after a failed deploy, an undo that didn’t undo, and a test helper that quietly gave you a 90-day login session. I’d want all three caught again.

Then the video relay went through twelve rounds of review at about 45 minutes a round. Most of the later objections were about what might go wrong while recovering from something else going wrong. Meanwhile, the channels were still broken. I stopped the loop, kept a copy of the old relay, and made sure I could put it back with one command. Then I did the swap. It worked the first time.

A worker telling a safety classifier “the owner approved this” got refused, even when I’d given the coordinator that exact approval on my phone. Annoying, and completely right. If any worker can say I approved something, what does my approval buy me?

The Mac had opinions too. At roughly twenty parallel agents it kernel-panicked, and I lost work I’d left in temporary storage. Eight test suites starting together pushed the load to 157 on a 14-core machine. Then there was “61 of 66 channels working.” The 66 were my favourites. An earlier run had reported 48 failures. Those were a bug in the measurement tool.

Now I keep it boring. Deploys take a lock and read the state they’re about to change. Sensitive approvals come straight from me. Three test-heavy workers at a time, with their work on persistent disk. I still want a second model to review the code. If we’re two rounds into edge cases and I can put the old version back with one command, I make the call.

And whenever an agent reports a number, I ask out of what.
