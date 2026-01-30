+++
title = "Cache Frontier, Part 1: Cold Starts"
date = 2026-01-20T09:00:00-08:00
draft = true
summary = "Why cold starts hit harder than expected and how we profiled the first miss."
series = ["Cache Frontier"]
+++

## Context

The cache looked healthy, yet cold starts were punishing. This entry documents the first pass and the profiling data.

## Notes

- Cold misses are rarely just cold.
- Measure before you tune.
- Make the baseline visible to everyone.
