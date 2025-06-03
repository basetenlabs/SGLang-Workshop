# 03 Faster model inference with CUDA graph

We want `cuda graph` to be `True` during decode, but by default the max batch 8 on L4.

When we set to 32, we are able to handle realistic batches during benchmark.

Video in this folder shows example run.

```bash
# benchmark cmd
lm_eval --model local-chat-completions --model_args model=meta-llama/Llama-3.1-8B-Instruct,base_url=http://127.0.0.1:8000/v1/chat/completions,num_concurrent=128,timeout=999999,max_gen_toks=2048 --tasks gsm8k --batch_size 128 --apply_chat_template --num_fewshot 8 --limit 0.15
```
