---
title: "What I Learned Reading About Grid Computing"
date: 2026-05-10
---

I came across grid computing while reading about distributed systems and went down a rabbit hole.

Grid computing is about pooling together resources from multiple machines, often across different locations, to work on a shared problem. Unlike a cluster where machines are tightly coupled, a grid is more loosely connected. Machines can join and leave.

Coming from parallel computing coursework, the tradeoffs felt familiar: communication overhead vs. compute gain, resource allocation under contention, the cost of coordination. But grid computing adds another layer because the machines are not necessarily in the same network or even the same organization.

What I want to explore next: how grid computing influenced early cloud architectures, the scheduling problem in heterogeneous grids, and whether any of these ideas show up in modern federated learning setups.
