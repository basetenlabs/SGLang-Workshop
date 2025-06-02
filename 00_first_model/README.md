# 00 Deploy your first model with SGLang

In this step, we'll get comfortable with the basic mechanics of SGLang.

## Deployment

With this folder as your working directory, run:

```
truss push . --publish
```

Go to your Baseten workspace to see live deployment logs.

## SGLang server command

```
sh -c "HF_TOKEN=$(cat /secrets/hf_access_token) python3 -m sglang.launch_server --model-path meta-llama/Llama-3.1-8B-Instruct --host 0.0.0.0 --port 8000 --served-model-name meta-llama/Llama-3.1-8B-Instruct --tp 1"
```

* `HF_TOKEN`: gives access to Llama model
* `--host` and `--port`: for Docker
* `--served-model-name`: sets model
* `--tp 1`: sets tensor parallelism equal to GPU count

## Truss configuration

These configuration details are specific to Baseten when running SGLang via Truss:

* **Model metadata:** Sets in-product playground
* **Resources:** Uses `accelerator` to set GPU type and count e.g. `H100_40GB` or `L4:2`
* **Predict concurrency:** Sets target request concurrency for autoscaling