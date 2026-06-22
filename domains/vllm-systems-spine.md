# vLLM Systems Spine

Use this when evaluating vLLM or similar LLM serving repositories.

## Purpose

Make the agent reason from LLM serving concepts before changing code. The goal
is to connect issues, papers, files, tests, and benchmarks to a shared systems
model.

## Core Concepts

| Concept | Why it matters for contributions |
|---|---|
| KV cache | Dominates memory during autoregressive decoding and shapes batching, scheduling, and prefix reuse decisions. |
| PagedAttention | Uses block-style KV cache management to reduce memory waste and support higher-throughput serving. |
| Continuous batching | Interleaves requests with different sequence lengths and decode progress; affects latency and throughput tradeoffs. |
| Scheduler | Decides which requests advance; changes can shift fairness, tail latency, preemption, and GPU utilization. |
| TTFT | Time to first token; key user-visible latency metric for prefill and queueing behavior. |
| TPOT | Time per output token; key decode throughput/latency metric. |
| ITL | Inter-token latency; useful for streaming user experience and decode jitter. |
| E2EL | End-to-end latency; captures the full serving path. |
| Prefix caching | Reuses previously computed KV state; changes can improve throughput but risk correctness/cache invalidation bugs. |
| Speculative decoding | Trades draft-model work for faster generation; eval must include acceptance rate and correctness. |
| Tensor parallelism | Splits model computation across devices; changes can affect communication and memory behavior. |
| Quantization | Reduces memory/bandwidth cost but can affect quality and kernel compatibility. |

## Contribution Surfaces

- docs and benchmark documentation
- scheduler behavior and queueing edge cases
- KV cache allocation, eviction, and prefix reuse
- metrics export and observability
- tests for correctness across model, device, and serving modes
- benchmark scripts and reproducibility
- compatibility docs for quantization, distributed serving, and hardware backends

## Issue Reading Questions

- Is the issue about correctness, performance, usability, observability, or docs?
- Which serving phase is touched: prefill, decode, scheduling, cache, or output?
- Which metric would move if the fix works?
- Which metric could regress?
- Does the issue require GPU/hardware validation?
- Is there a smaller docs/test/repro packet before a code patch?

## Eval Dimensions

| Dimension | Examples |
|---|---|
| Correctness | unit tests, integration tests, output consistency, cache validity |
| Latency | TTFT, TPOT, ITL, E2EL, p50/p95/p99 |
| Throughput | requests/sec, output tokens/sec, total tokens/sec |
| Memory | peak GPU memory, KV cache utilization, fragmentation, preemption |
| Quality | task metric, judge score, exact match, regression set |
| Operability | metrics, logs, docs clarity, failure messages |
| Maintainer fit | issue scope, style match, reviewability, test burden |

## Source Loading Prompts

```markdown
Before editing, identify:

- serving phase:
- affected system surface:
- likely metric:
- likely regression risk:
- nearest tests:
- nearest benchmark:
- relevant paper or design doc:
- minimum public contribution packet:
```

## Evidence Standard

Do not claim "improves vLLM performance" without a benchmark or a very explicit
docs/test-only scope. Prefer language like:

- "adds validation coverage for..."
- "documents the expected metric interpretation for..."
- "reduces ambiguity around..."
- "reproduces a scheduler edge case under..."
- "measures TTFT/TPOT before and after under..."

## Starting References

- [Efficient Memory Management for Large Language Model Serving with PagedAttention](https://arxiv.org/abs/2309.06180)
- [vLLM metrics documentation](https://docs.vllm.ai/en/stable/design/metrics/)
- [vLLM benchmark serve CLI](https://docs.vllm.ai/en/stable/cli/bench/serve/)
