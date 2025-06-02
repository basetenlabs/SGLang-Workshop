# SGLang Workshop

*AI Engineer World's Fair, June 3, 2025*

Welcome to the SGLang workshop at AI Engineer World's Fair! 
We are very excited to have you here and to spend some time this morning
talking about model performance optimization with SGLang.

## Developer setup

In this hands-on workshop, you'll have the ability to deploy models with SGLang yourself.
To follow along, please complete the following steps:

1. Fork and clone this repository.
2. Create a Baseten account.
   1. Baseten will provide compute credits for this workshop.
   2. If you're stuck in a "waiting room" for more than a couple of minutes, please flag Philip.
3. Install Truss with `pip install --upgrade truss`

### Required: Get access to Llama 3.1 8B

These workshop examples are based on Llama 3.1 8B. 

1. Accept the terms and conditions for [Llama 3.1 8B](https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct).
2. Create an [access token](https://huggingface.co/settings/tokens) with `READ` permissions on Hugging Face.
3. Add it as a [secret on your Baseten account](https://app.baseten.co/settings/secrets) with the name `hf_access_token`.

### Recommended: Set up your Baseten API key

Create a file `~/.trussrc` and paste in the following (using your actual API key):

```
[baseten]
remote_provider = baseten
api_key = abcdefgh.1234567890ABCDEFGHIJKL1234567890
remote_url = https://app.baseten.co
```

Add your API key to your environment variables in your profile of choice:

```
export BASETEN_API_KEY=abcdefgh.1234567890ABCDEFGHIJKL1234567890
```

You are now ready to complete the workshop.

## Deploying models

Each folder has an example SGLang configuration along with instructions for deployment.

## Calling models

Use `call.ipynb` to call individual deployments. Models deployed with SGLang are compatible
with the OpenAI SDK -- just pass your model ID and API key.