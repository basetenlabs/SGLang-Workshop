# 03 Faster model inference with CUDA graph

We want `cuda graph` to be `True` during decode, but by default the max batch 8 on L4.

When we set to 32, we are able to handle realistic batches during benchmark.

Video in this folder shows example run.