# Thinkube AI Examples

Working examples for building AI applications on the Thinkube platform.

**License**: Apache License 2.0
**Copyright**: 2025 Alejandro Martínez Corriá

## Purpose

This repository contains two examples. `research-assistant/` builds an AI Research Lab Assistant across four notebooks. `zebra-grpo/` fine-tunes a model on rewards a program can check, registers it, and serves it — the full loop from a base model to a served one.

## Structure

```
thinkube-ai-examples/
├── research-assistant/
    ├── 00-platform-validation.ipynb  # Validate platform services
    ├── 01-register-litellm.ipynb     # Register LLM models
    ├── 02-langchain-rag.ipynb        # RAG pipeline for paper search
    └── 03-multi-agent.ipynb          # Multi-agent coordination
└── zebra-grpo/
    ├── zebra_grpo.ipynb              # Fine-tune on verifiable rewards, register, serve
    └── zebra_dataset.py
```

## The Application: AI Research Lab Assistant

An AI assistant for managing ML/AI research papers that:

- **Ingests ArXiv papers** - PDF loading and text extraction
- **Semantic search** - Find papers by meaning, not just keywords
- **Answers questions** - RAG-powered Q&A about research
- **Summarizes papers** - Extract key findings
- **Multi-agent coordination** - Paper Summarizer, Experiment Tracker, Insight Finder
- **Links to MLflow** - Connect papers to experiments

## Platform Services Used

All notebooks integrate with these Thinkube services:

| Service | Purpose |
|---------|---------|
| LiteLLM | Unified LLM gateway |
| Qdrant | Vector database for RAG |
| Langfuse | Observability and tracing |
| MLflow | Experiment tracking |
| PostgreSQL | Paper metadata storage |
| Valkey | Caching |
| NATS | Multi-agent messaging |

## Prerequisites

- JupyterHub access on Thinkube platform
- `tk-jupyter-agent-dev` image (for notebooks 00, 01, 02, 03)
- `tk-jupyter-fine-tuning` image (for notebook 04)

## Getting Started

1. Open JupyterHub: `https://jupyter.{your-domain}`
2. Select `tk-jupyter-agent-dev` image
3. Navigate to `research-assistant/`
4. Start with `00-platform-validation.ipynb` to verify services
5. Work through notebooks in order (00 → 04)

## Development Approach

These notebooks are built using **documentation-driven development**:

1. Each notebook contains working, tested code
2. Code is validated against actual platform services
3. Outputs and results are real, not mocked
4. Issues encountered are documented

## Related Documentation

- [Implementation Plan](https://github.com/thinkube/thinkube-documentation/blob/main/IMPLEMENTATION_PLAN.md)
- [Platform Services Integration](https://github.com/thinkube/thinkube-documentation/blob/main/guides/platform-services-integration.md)
