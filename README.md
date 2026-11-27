# stellargibbon

ML infra. Quantized GEMM kernels, multi-node LLM serving.

## Projects

- [W4A16-GEMM](https://github.com/Stellargibbon/W4A16-GEMM) - replication of a W4A16 GEMM kernel on RTX 3070 (sm_86): prediction-ledger vs measured, found GeForce Ampere doesn't halve FP16-accum mma (~40.9 TFLOPS real ceiling)
- [gpt-roofline](https://github.com/Stellargibbon/gpt-roofline) - GPT-2 training + MFU roofline on OpenWebText, measured end to end
- [micro-gpt](https://github.com/Stellargibbon/micro-gpt) — char-level GPT from scratch, 9 tested components; causal-mask leak debug writeup
- GLM-5.3-Flash on 2x DGX Spark (TensorFold) - 18 → 54 tok/s decode via speculative-decoding env profiling
- Qwen3.8-Flash-Next serving A/B on a Spark pair - NVFP4 vs EXL3, TTFT + decode characterized

## Working on

- **Switchless 6x DGX Spark ring** — GLM-5.3 4-bit serving across 6 nodes, no switch.
  Custom NCCL ring topology; builds on the TP=2 pair work above.
