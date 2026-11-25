---
layout: post
title: "Why did checking the mail take a billion tokens?"
date: 2026-11-24
homepage_summary: Four agents spent 1.1 billion tokens watching mailboxes. A file-change event could have told them when a reply needed a decision.
---

I gave three coding agents Markdown mailboxes and spent two weeks building Jarvis, one interface for the TV, lights, cameras, and music in our house. The logs came to 28.5 billion tokens. Four watcher agents burned 1.1 billion of them just checking whether the others had replied. The coordinator burned another 3.1 billion in a single session.

How does checking a file get that expensive? Every time a watcher woke up, the model re-read its entire context. The coordinator did the same thing with diffs, test logs, and mailbox threads, averaging nearly half a million input tokens per call. Across the build, 98.7% of the tokens were cache reads. Cache reads were cheap per token. We still hit Codex’s weekly cap twice.

The mistake was giving an agent a job with no natural end. "Watch this mailbox" can run forever and be correct on every turn. A coordinator that never rotates accumulates the history of the whole project until every routine check carries a half-million-token tax.

Teams keep deploying LLMs as persistent daemons: heartbeats, watchers, and long-lived managers sitting in a `while True` loop. A language model is a context-priced decision function, not a daemon. Deterministic code should own the waiting, the polling, and the event triggers. The model should only wake up when state changes and there is an actual judgment call to make.

I'd still give a difficult bug to a second agent. I'd give it a specific question, bound its session, and let it finish. The next time the mailbox changes, the filesystem can tell me for free.
