+++
title = "Cache Frontier, Part 2: Warming Strategy"
date = 2026-01-27T09:00:00-08:00
draft = true
summary = "We moved from reactive to proactive warming and captured the tradeoffs."
series = ["Cache Frontier"]
+++

## Context

We tested pre-warm strategies, learned where they helped, and documented the risks they introduced.

## Notes

- Warm selectively, not globally.
- Protect the database from the warm-up surge.
- Treat warmers as production code.
