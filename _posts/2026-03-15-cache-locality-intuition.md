---
title: "Building Intuition for Cache Locality"
date: 2026-03-15
---

One of the most useful things I picked up from my parallel computing course is thinking about how data moves through memory, not just what the algorithm does logically.

When I benchmarked all six loop orderings for matrix multiplication, the performance difference was massive, even though every ordering produces the exact same result. The only difference was memory access patterns. Sequential access along rows in row-major storage gave the best cache hit rates. Striding across columns destroyed performance.

It changed how I look at code. Now I think about where the data lives and how it flows, not just the Big-O complexity.
