# Llama 2 Resources

## Free playgrounds

* 70B-chat by Yuvraj at Hugging Face: https://huggingface.co/spaces/ysharma/Explore_llamav2_with_TGI
* 13B-chat by Hugging Face: https://huggingface.co/spaces/huggingface-projects/llama-2-13b-chat
* 7B-chat by Hugging Face: https://huggingface.co/spaces/huggingface-projects/llama-2-7b-chat
* 7B-chat, 13B-chat and 70B-chat by a16z: https://llama2.ai
* 13B-chat by [Pietro](https://twitter.com/skirano/status/1681381051237556224): https://llama-2.replit.app

## Running it yourself on a cloud GPU

* 70B GPTQ version required 35-40 GB VRAM. Follow this [guide](https://gpus.llm-utils.org/running-llama-2-on-runpod-with-oobaboogas-text-generation-webui/)

## Hosted APIs

* 70B chat: https://replicate.com/replicate/llama70b-v2-chat
* 13B chat: https://replicate.com/a16z-infra/llama13b-v2-chat

## Best model versions to use

* For minimal VRAM:
  * 7B GGML versions:
    * Chat-tuned model: https://huggingface.co/TheBloke/Llama-2-7B-Chat-GGML
    * Base model: https://huggingface.co/TheBloke/Llama-2-7B-GGML
  * 13B GGML versions:
    * Chat-tuned model: https://huggingface.co/TheBloke/Llama-2-13B-chat-GGML
    * Base model: https://huggingface.co/TheBloke/Llama-2-13B-GGML
* For large VRAM:
  * 70B GPTQ versions:
    * Chat-tuned version: https://huggingface.co/TheBloke/Llama-2-70B-chat-GPTQ
    * Base model: https://huggingface.co/TheBloke/Llama-2-70B-GPTQ

See more on GPTQ vs GGML versions of models [here](https://gpus.llm-utils.org/gptq-vs-ggml-vs-base-models/).

<!-- Benchmarks and leaderboards: -->

<!-- 7B vs 13B vs 70B: -->

## What about 34B?

It's coming soon. They wanted more time to red-team it.

## Chat vs Base

The base models are uncensored, and are not instruct-tuned or chat-tuned.

The chat models are censored, and have been chat-tuned.

### Are the base models instruct-tuned?

No.[^base-models] "These models are not finetuned for chat or Q&A. They should be prompted so that the expected answer is the natural continuation of the prompt."

### How can I prompt the base models?

Create a fake document so that if the model naturally continues what would be expected next in the document, you get the result you want. For example, instead of "What is the capital of France?" you'd write "The capital of France is "

See also: https://youtu.be/bZQun8Y4L2A?t=555

[^base-models]: https://github.com/facebookresearch/llama#pretrained-models

### Are they censored?

Base is uncensored, chat is censored.

## Prompt template

```text
<s>[INST] <<SYS>>
{your_system_message}
<</SYS>>

{user_message_1} [/INST]
```

and

```text
<s>[INST] <<SYS>>
{your_system_message}
<</SYS>>

{user_message_1} [/INST] {model_reply_1}</s><s>[INST] {user_message_2} [/INST]
```

See [here](https://gpus.llm-utils.org/llama-2-prompt-template/).

## Setting up an API endpoint

* [Hugging Face](https://huggingface.co/blog/llama2#using-text-generation-inference-and-inference-endpoints)
* Docker/Runpod - see [here](https://gpus.llm-utils.org/running-llama-2-on-runpod-with-oobaboogas-text-generation-webui/) but use [this](https://runpod.io/gsc?template=f1pf20op0z&ref=eexqfacd) runpod template instead of the one linked in that post

## What will some popular uses of Llama 2 be?

1. Devs playing around with it
2. Uses that GPT doesn't allow but are legal (for example, NSFW content)
3. Enterprises using it as an alternative to GPT-3.5 if they can get it to be cheaper overall
4. Enterprises using it as an alternative to GPT-4 if they can fine-tune it for a specific use case and get comparable performance

## Fine-tuning

* https://huggingface.co/blog/llama2#fine-tuning-with-peft
* https://github.com/facebookresearch/llama-recipes/tree/main#fine-tuning
* https://www.reddit.com/r/LocalLLaMA/comments/153qjdx/finetuning_llama_2_the_base_models/

## Fine-tuning as a service for enterprises

* Databricks (Patrick, co-founder, and Xiangrui, ML Lead) incl Mosaic ML
* Lamini.ai (Lamini is a Llama inspired name. Llamas, Alpacas, Vicuñas and Guanacos are all subsets of the Lamini tribe.)
* Radiant AI
* Scale AI
* Snowflake

## Running locally

* https://www.reddit.com/r/LocalLLaMA/comments/153o791/llama2_via_mlc_llm/
* https://gist.github.com/adrienbrault/b76631c56c736def9bc1bc2167b5d129
