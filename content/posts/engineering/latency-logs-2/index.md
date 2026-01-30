+++
title = "Latency Logs, Part 2: The Hidden Queue"
date = 2026-01-17T08:30:00-08:00
draft = true
summary = "We found the hidden queue that stretched tail latency. Fixes, tradeoffs, and what we learned."
series = ["Latency Logs"]
+++

## Context

The culprit wasn’t the database; it was the queue between two services. This entry documents how we proved it.

## Notes

- Queue depth lies unless you account for retries.
- Small concurrency changes can create big tail effects.
- Make the fix reversible.
