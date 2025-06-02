# 02 Faster model inference with Eagle 3

In this step, we'll use Eagle 3 to accelerate inference via speculation

## Deployment

With this folder as your working directory, run:

```
truss push . --publish
```

Go to your Baseten workspace to see live deployment logs.

## SGLang server command

```
sh -c "sh -c "HF_TOKEN=$(cat /secrets/hf_access_token) python3 -m sglang.launch_server --model-path meta-llama/Llama-3.1-8B-Instruct --host 0.0.0.0 --port 8000 --served-model-name meta-llama/Llama-3.1-8B-Instruct --tp 2 --speculative-algorithm EAGLE --speculative-draft-model-path lmsys/sglang-EAGLE3-LLaMA3.1-Instruct-8B --speculative-num-steps 3 --speculative-eagle-topk 1 --speculative-num-draft-tokens 4 --dtype float16"
```

* `HF_TOKEN`: gives access to Llama model
* `--host` and `--port`: for Docker
* `--served-model-name`: sets model
* `--tp 2`: sets tensor parallelism equal to GPU count (in this case 2 L4s)
* `--speculative-algorithm`: Specifies EAGLE
* `--speculative-draft-model-path`: Loads LMSYS-provided draft model
* `--speculative-num-steps`: Depth of drafting
* `--speculative-eagle-topk`: Branching factor per step
* `--speculative-num-draft-tokens`: Maximum parallel verification

Further reading: [https://docs.sglang.ai/backend/speculative_decoding.html#EAGLE-Decoding](https://docs.sglang.ai/backend/speculative_decoding.html#EAGLE-Decoding)

## Truss configuration

These configuration details are specific to Baseten when running SGLang via Truss:

* **Model metadata:** Sets in-product playground
* **Resources:** Uses `accelerator` to set GPU type and count e.g. `H100_40GB` or `L4:2`
* **Predict concurrency:** Sets target request concurrency for autoscaling