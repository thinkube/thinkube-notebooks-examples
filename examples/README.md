# Thinkube Notebooks Examples

Working examples for building AI applications on the Thinkube platform. Each notebook runs against the services of your own cluster, and the outputs saved in them are from real runs.

**License**: Apache License 2.0
**Copyright**: 2025 Alejandro Martínez Corriá

## What is here

Two examples. `research-assistant/` builds an assistant over a corpus of research papers in four notebooks, run in order. `zebra-grpo/` fine-tunes a model on rewards a program can check, registers it and serves it: the loop from a base model to one you serve yourself.

```
examples/
├── research-assistant/
│   ├── 00-platform-validation.ipynb  # Check the platform services the notebooks use
│   ├── 01-load-models.ipynb          # Load a chat model and an embedding model through the LLM Gateway
│   ├── 02-langchain-rag.ipynb        # Index arXiv papers in Qdrant and answer questions with sources
│   └── 03-multi-agent.ipynb          # Two agents debate from the index; a judge decides
└── zebra-grpo/
    ├── zebra_grpo.ipynb              # Fine-tune with GRPO, register in Thinkube Experiments, serve
    └── zebra_dataset.py
```

## Kernels and services

| Notebook | Kernel | Services |
|---|---|---|
| 00-platform-validation | `agent-dev` | LLM Gateway, Qdrant, Langfuse, Thinkube Experiments (MLflow), PostgreSQL, Valkey, NATS; a service that is not installed is skipped |
| 01-load-models | `agent-dev` | LLM Gateway, through `tk-llm` |
| 02-langchain-rag | `agent-dev` | LLM Gateway, Qdrant, Langfuse, the arXiv API |
| 03-multi-agent | `agent-dev` | LLM Gateway (a model with tool calling), Qdrant, Langfuse |
| zebra-grpo | `fine-tuning`, one GPU with about 20 GB free | Thinkube Experiments, the LLM Gateway, Hugging Face for the benchmark dataset |

Install Qdrant and Langfuse before the research assistant; ask Claude Code: "install Qdrant and Langfuse".

## Getting started

1. Open Thinkube Notebooks at `https://notebooks.<your domain>` and start a server; pick a GPU node for `zebra-grpo`.
2. Open `examples/research-assistant/00-platform-validation.ipynb` with the `agent-dev` kernel.
3. Run 00, 01, 02 and 03 in order; 01 leaves the models loaded for 02 and 03.
4. Then open `examples/zebra-grpo/zebra_grpo.ipynb` with the `fine-tuning` kernel.

Your copy in `notebooks/examples/` is made once, the first time your server starts, and is yours to change. A fresh copy of this repository is in `templates/examples/` every time the server starts; copy a notebook from there to take a newer version.

## Documentation

The Thinkube documentation, at `https://docs.<your domain>` on your cluster, covers these notebooks under Thinkube Models: *The example notebooks*, *Build a research assistant, end to end* and *Fine-tune on verifiable rewards, end to end*. Or ask Claude Code: "how do I run the research assistant notebooks?"
