# Reproducible LLM Workflows with Ollama

Practical guide to building reliable Large Language Model workflows using a fully local setup.

**Author:** Dr. Jean-Jacques Ponciano

---

## Overview

This repository provides a clear and reproducible introduction to working with Large Language Models (LLMs) using the Ollama local API.

The focus is practical. Instead of theory, the goal is to show how to build usable and reliable systems based on:

- local execution (no cloud dependency)
- API-first interaction
- controlled prompting
- structured outputs
- reproducible pipelines

---

## Why this repository

Most tutorials focus on prompting alone.  
This repository goes further and shows how to build **complete workflows**, including:

- prompt design
- output structuring
- evaluation
- decision support
- context injection
- retrieval-augmented generation (RAG)

---

## What you will learn

By following this repository, you will be able to:

- interact with a local LLM through an API
- control model behavior using system prompts
- generate structured outputs (JSON)
- build classification and decision systems
- evaluate model outputs
- distinguish context injection from RAG
- implement a minimal local RAG pipeline

---

## Requirements

- macOS / Linux / Windows
- Python 3.9+
- Ollama installed

👉 Download Ollama: https://ollama.com

---

## Quick Start

### 1. Start Ollama

```bash
ollama serve
````

---

### 2. Pull a model

```bash
ollama pull qwen2.5:3b
```

---

### 3. Test the API

```bash
curl http://localhost:11434/api/chat -d '{
  "model": "qwen2.5:3b",
  "stream": false,
  "messages": [
    {"role": "user", "content": "Explain gravity simply."}
  ]
}'
```

---

## Repository Structure

```bash
.
├── README.md
├── LICENSE
├── tutorial.md
├── minimal_rag.py
├── ollama_chat.py
```

---

## Tutorial

The main tutorial is available here:

👉 [tutorial.md](./tutorial.md)

It covers:

* prompting fundamentals
* structured outputs
* classification and evaluation
* context injection
* full local RAG pipeline

---

## Minimal RAG Example

### Install dependencies

```bash
pip install numpy requests
```

---

### Install embedding model

```bash
ollama pull nomic-embed-text
```

---

### Run

```bash
python minimal_rag.py
```

---

## Key Concepts

### Prompting

Control behavior using:

* system → role and constraints
* user → task

---

### Structured Outputs

Example:

```json
"Output only valid JSON."
```

---

### Context vs RAG

| Approach          | Description                   |
| ----------------- | ----------------------------- |
| Context injection | Manual context in prompt      |
| RAG               | Automatic retrieval from data |

---

## Best Practices

* keep prompts explicit
* constrain output formats
* validate JSON outputs
* separate retrieval from generation
* test multiple inputs
* measure consistency

---

## Common Mistakes

* confusing context injection with RAG
* assuming the model has memory
* trusting outputs without validation
* using small models for complex reasoning

---

## Limitations

This repository focuses on local and reproducible workflows.

It does not cover:

* fine-tuning
* large-scale vector databases
* advanced agent systems

---

## License

MIT License — see [LICENSE](./LICENSE)

---

## Citation

If you use this work:

```
Ponciano, J.-J. (2026). Reproducible LLM Workflows with Ollama.
```

---
