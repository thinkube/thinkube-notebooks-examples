# CLAUDE.md

Guidance for Claude Code when working with these notebooks.

## What is here

```
examples/
├── research-assistant/
│   ├── 00-platform-validation.ipynb  # Checks LLM Gateway, Qdrant, Langfuse, MLflow, PostgreSQL, Valkey, NATS
│   ├── 01-register-litellm.ipynb     # Loads a chat and an embedding model through the LLM Gateway (tk-llm)
│   ├── 02-langchain-rag.ipynb        # arXiv corpus -> chunks -> embeddings -> Qdrant collection rl_reasoning_papers
│   └── 03-multi-agent.ipynb          # AG2 debate citing the Qdrant index; a judge decides
└── zebra-grpo/
    ├── zebra_grpo.ipynb              # GRPO fine-tune of unsloth/Qwen3.5-4B, registered in MLflow, served via the gateway
    └── zebra_dataset.py
```

Kernels: `agent-dev` for the research assistant, `fine-tuning` for zebra-grpo.

## Platform services

| Service | How a notebook reaches it |
|---|---|
| LLM Gateway | `tk_llm`: `LLMClient()` to list, load and unload models; `get_openai_client()` for chat and embeddings |
| Qdrant | `QDRANT_URL` |
| Langfuse | `LANGFUSE_HOST`, `LANGFUSE_PUBLIC_KEY`, `LANGFUSE_SECRET_KEY` |
| Thinkube Experiments (MLflow) | `MLFLOW_TRACKING_URI`; `thinkube_models` for the token and the model staging path |
| PostgreSQL | `POSTGRES_*` |
| Valkey | `VALKEY_HOST`, `VALKEY_PORT`, `VALKEY_PASSWORD` |
| NATS | `NATS_URL` |

The variables are injected by Thinkube Notebooks; a service that is not installed has no variables.

## Rules for changes

1. Every cell must execute against the real services; no stubs, no mocks.
2. Saved outputs are from real runs; rerun a notebook after changing it.
3. Run notebooks over MCP when no browser is needed: `jupyter_use_notebook`, then `jupyter_execute_all_cells`, with paths relative to the notebooks folder, for example `examples/research-assistant/00-platform-validation.ipynb`.
