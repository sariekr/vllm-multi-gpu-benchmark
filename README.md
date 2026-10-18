# vLLM Multi-GPU Benchmark

AIMultiple study of Llama-3.1-8B-Instruct inference across one, two, four and eight GPUs. It measures how independent vLLM replicas scale on H100, H200, B200 and MI300X systems.

> [Read the benchmark on AIMultiple](https://aimultiple.com/multi-gpu)

## Scaling results

The workload uses 10,000 ShareGPT prompts. Data parallelism runs a complete model copy on each GPU and divides the requests across those copies.

Published total throughput:

| GPU | One GPU (tokens/s) | Eight GPUs (tokens/s) | Scaling efficiency |
| --- | ---: | ---: | ---: |
| H100 | 23,243 | 147,606 | 79% |
| H200 | 25,387 | 150,391 | 74% |
| B200 | 34,249 | 172,470 | 63% |
| MI300X | 18,752 | 101,069 | 67% |

Efficiency is eight-GPU throughput divided by eight times the single-GPU result. B200 has the highest total throughput in this table. H100 retains the largest share of ideal scaling.

These measurements cover a model that fits on one GPU. Host resources and serving settings affect scaling. Tensor parallelism, which splits a model across GPUs, has a limited reference comparison in the article.

## Ownership

The benchmark implementation was developed for AIMultiple and belongs to AIMultiple. This repository contains a documentation summary. Source code and benchmark datasets are not distributed here.
