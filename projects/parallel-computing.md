---
title: Parallel & Distributed Computing Studies
permalink: /projects/parallel-computing/
---

<a class="home-link" href="/">Home</a>

# Parallel & Distributed Computing Studies

Explorations in hardware-aware optimization, concurrency, and performance modeling from coursework at UC Irvine.

---

## Hardware-Aware Parallel Matrix Multiplication

### Problem

Understanding how loop ordering, cache behavior, and thread scaling affect dense matrix multiplication performance on modern hardware.

### Approach

- Analyzed all 6 loop orderings (i,j,k permutations) for cache efficiency in row-major storage.
- Identified scalar reuse and sequential memory access as the primary performance drivers.
- Benchmarked multi-threaded execution on Apple M-series silicon across matrix sizes up to 2048x2048 and thread counts up to 16.
- Applied Amdahl's Law to characterize parallelization limits from memory bus contention and synchronization overhead.
- Mapped computation to an n-processor ring topology, analyzing memory vs. communication tradeoffs: O(n) memory, O(n^2) communication as the optimal efficiency frontier.

### Results

Achieved **4.55x speedup at 8 threads**. Performance plateaued beyond 8 threads due to memory bandwidth saturation on the shared bus.

<div class="badge-row">
  <span class="badge">C</span>
  <span class="badge">pthreads</span>
  <span class="badge">Cache Optimization</span>
  <span class="badge">Amdahl's Law</span>
</div>

---

## Shared-Memory Distributed System Simulation

### Problem

Modeling how processor count, memory module allocation, and access patterns affect throughput and contention in shared-memory architectures.

### Approach

- Simulated K processors and M single-ported memory modules with an interconnection network.
- Compared uniform distribution vs. normal distribution (locality of reference) memory access patterns.
- Plotted average wait time against M from 1 to 2048 for processor counts from 2 to 64.
- Identified saturation points for cost-effective memory module allocation.
- Demonstrated the necessity of non-starving assignment schemes during high-contention cycles.

### Results

Established clear scaling curves showing **diminishing returns past specific memory-to-processor ratios**, with locality-aware access patterns significantly reducing contention.

<div class="badge-row">
  <span class="badge">Simulation</span>
  <span class="badge">Shared Memory</span>
  <span class="badge">Performance Modeling</span>
  <span class="badge">Contention Analysis</span>
</div>

---

## Parallel Prime Calculation & Heterogeneous Core Analysis

### Problem

Investigating thread scaling behavior and hardware heterogeneity effects on lock-based parallel workloads.

### Approach

- Implemented multithreaded prime calculation using pthreads and mutex synchronization.
- Analyzed Apple M4 Pro heterogeneous core architecture: 8 Performance cores and 4 Efficiency cores.
- Measured how slower E-cores holding shared locks stalled faster P-cores, creating asymmetric bottlenecks.

### Results

Maximum speedup of **1.233x at 2 threads**. Performance degraded beyond that due to lock contention across heterogeneous cores. Optimal throughput requires staying within the performance core envelope.

<div class="badge-row">
  <span class="badge">pthreads</span>
  <span class="badge">Mutex</span>
  <span class="badge">Apple M4 Pro</span>
  <span class="badge">Heterogeneous Computing</span>
</div>

---

## Technology Stack

C, Python, pthreads, mutex synchronization, Apple M-series / M4 Pro silicon, performance benchmarking

---

<div class="cta-row">
  <a class="btn btn-primary" href="/projects.html">Back to Projects</a>
  <a class="btn btn-primary" href="/">Back to Home</a>
</div>
