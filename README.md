# Hi, I'm stellargibbon

ML infrastructure / inference-systems person. Find-the-bottleneck-and-kill-it work:
quantized GEMM kernels, multi-node LLM serving, and measuring the things vendor
slides skip.

**Home fleet: 6x NVIDIA DGX Spark (GB10, 128 GiB unified memory each)** --
switchless ConnectX-7 rings, TP=2 serving pairs over RoCE, and benchmarks on this
hardware class you won't find published anywhere else.

## Recent work

- **[W4A16-GEMM](https://github.com/Stellargibbon/W4A16-GEMM)** -- replicating
  W4A16 quantized-GEMM performance floors (decode ~88-90%, prefill ~83% MFU) on
  Blackwell-class consumer silicon.
- **[gpt-roofline](https://github.com/Stellargibbon/gpt-roofline)** -- GPT-2-scale
  training pipeline + MFU roofline measurement on OpenWebText. Measured, not
  estimated: loaders cold-pass profiled, eval-selection bias under 0.0115.
- **vLLM #56830** (upstream thread) -- root-caused a profiling-phase OOM runaway
  on unified-memory GB10s: 9 boots / 7 configs / 0 startups, kernel oom-kill
  receipts, shmem-accounting diagnosis (unified-memory CUDA allocations surface
  as shm). Ongoing with maintainers.
- **GB10 launch-cost replication** (peer benchmark run, 3 GPUs) -- found a
  constant ~2.27 ms per-launch host cost on GB10 with SM clocks pinned the whole
  run (so: not DVFS), collapsing to ~1 us under CUDA graphs. Replicated on two
  independent boxes. Writeup in progress.

## Currently building

A 4-node switchless ring for 750B-class model serving -- then the first published
6-node switchless-ring experiments.

<!--
Mine: numbers over adjectives. Every claim above links to receipts.
-->
