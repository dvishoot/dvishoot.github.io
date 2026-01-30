+++
title = "Latency Logs, Part 1: The 2 a.m. Spike"
date = 2026-01-10T08:30:00-08:00
draft = true
summary = "A sudden spike turned a quiet on-call shift into a forensic session. Here’s the first sweep."
series = ["Latency Logs"]
+++

## Context

We saw a sharp p95 jump right after a deploy. This entry captures the first pass: dashboards, hypotheses, and the real-time constraints of incident response.

## Notes

- Start with the symptom, not the suspected cause.
- Stabilize SLOs before optimizing anything else.
- Log questions and assumptions as you go.
