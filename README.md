<div align="center">

# Qwen 3.8 · 27B on Ollama

Run the OrcaRouter Qwen 3.8 27B Uncensored build locally with a 4K context window and thinking mode off.

**Q3_K_M · ~14 GB download · macOS / Linux / Windows**

[Quick start](#quick-start) · [Smoke test](#smoke-test) · [Troubleshooting](#troubleshooting)

</div>

---

## Quick start

**Already have the local model?** Start it directly:

```sh
ollama run --think=false qwen3.8:27b-uncensored
```

**Setting up on a new machine?**

1. [Install Ollama](https://ollama.com/download) and open the app. If you installed only the CLI, run `ollama serve` in a separate terminal.
2. Open a terminal in this repository. With about 14 GB of free disk space for the download, plus some headroom, run these commands in order:

   ```sh
   ollama pull orcarouter/Qwen3.8-27B-Uncensored:q3_k_m
   ollama create qwen3.8:27b-uncensored -f Modelfile
   ollama run --think=false qwen3.8:27b-uncensored
   ```

   `ollama create` uses the downloaded weights and applies the settings in [Modelfile](Modelfile). Run it only if you want to create or replace that local tag. Type `/bye` to exit the chat.

## Smoke test

After setup, run a single prompt without opening an interactive session:

```sh
ollama run --think=false qwen3.8:27b-uncensored "Reply with exactly: Hello from Ollama."
```

## Troubleshooting

| If you see… | Try this |
| --- | --- |
| Ollama cannot connect | Open the Ollama app or start `ollama serve` in a separate terminal. Then run `ollama list`. |
| The local model name is missing | Complete the pull and create steps. `qwen3.8:27b-uncensored` is the local name created by this guide. |
| Ollama does not recognize `--think` | Update Ollama from the [official download page](https://ollama.com/download). |
| The model runs slowly or runs out of memory | Close other memory-heavy apps. Use `ollama ps` to see how much of a running model is on the CPU or GPU. If needed, lower `num_ctx` in the Modelfile and rerun `ollama create`. The download size is not a runtime memory requirement. |

## Model and configuration

The [OrcaRouter model card](https://ollama.com/orcarouter/Qwen3.8-27B-Uncensored) lists available builds and the model’s Apache 2.0 license. This repository contains only setup files. The Modelfile shares the original setup’s model weights, context size, and sampling settings; any custom system prompt and machine-specific CPU or GPU settings stay local. The [Ollama thinking guide](https://docs.ollama.com/capabilities/thinking) explains how thinking controls work.
