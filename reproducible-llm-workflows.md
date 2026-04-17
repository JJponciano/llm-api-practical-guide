# Reproducible LLM Workflows with Ollama

**Practical, local, and API-first guide to Large Language Models**

**Author:** Dr. Jean-Jacques Ponciano

---

## Overview

This repository provides a clear and reproducible introduction to working with Large Language Models (LLMs) using the local Ollama API.

It focuses on practical usage rather than theory, showing how to build reliable workflows using only:

```bash
http://localhost:11434/api/chat
````

The objective is to demonstrate how LLMs can be used as:

* reasoning systems
* data processing tools
* decision-support components
* evaluation engines
* pipeline orchestrators

---

## Features

* Fully local setup (no cloud dependency)
* Reproducible examples using curl and Python
* Clear separation between prompting, structure, and retrieval
* Minimal but complete RAG pipeline
* Ready-to-use scripts

---

## Quick Start

### 1. Install Ollama

Download and install Ollama:

[https://ollama.com](https://ollama.com)

---

### 2. Run Ollama

```bash
ollama serve
```

---

### 3. Pull a model

```bash
ollama pull qwen2.5:3b
```

---

### 4. Test API

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

```
.
├── README.md
├── minimal_rag.py
├── ollama_chat.py
└── examples/
```

---

## Core Concepts

### 1. Prompting

LLM interaction is based on:

* system → behavior
* user → task
* assistant → memory

---

### 2. Output Control

You can control structure:

```json
"Output only valid JSON."
```

---

### 3. Context vs RAG

| Method            | Description                          |
| ----------------- | ------------------------------------ |
| Context injection | Manually provide data                |
| RAG               | Retrieve relevant data automatically |

---

## Examples

### Basic Prompt

```bash
curl http://localhost:11434/api/chat -d '{
  "model": "qwen2.5:3b",
  "stream": false,
  "messages": [
    {"role": "user", "content": "Why is the sky blue?"}
  ]
}'
```

---

### JSON Extraction

```bash
curl http://localhost:11434/api/chat -d '{
  "model": "qwen2.5:3b",
  "stream": false,
  "messages": [
    {"role": "system", "content": "Output only JSON."},
    {"role": "user", "content": "Alice is 32 years old."}
  ]
}'
```

---

### Classification

```bash
curl http://localhost:11434/api/chat -d '{
  "model": "qwen2.5:3b",
  "stream": false,
  "messages": [
    {"role": "system", "content": "Classify sentiment."},
    {"role": "user", "content": "The product is good but delivery is slow."}
  ]
}'
```

---

## Minimal RAG Pipeline

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

### Pipeline

```
Documents → Embeddings → Retrieval → Context → LLM
```

---

## Python Wrapper

```python
import requests

def chat(model, messages):
    return requests.post(
        "http://localhost:11434/api/chat",
        json={"model": model, "messages": messages, "stream": False}
    ).json()
```

---

## Best Practices

* keep prompts explicit
* constrain outputs
* validate JSON
* separate retrieval from generation
* test multiple cases
* measure consistency

---

## Common Mistakes

* confusing RAG with context injection
* assuming persistent memory
* trusting outputs blindly
* using small models for complex reasoning

---

## Limitations

This repository does not cover:

* fine-tuning
* large-scale vector databases
* advanced agent frameworks

It focuses on **local reproducible workflows**.

---

## Benchmarking

Recommended test categories:

* explanation
* extraction
* classification
* evaluation
* RAG

Metrics:

* correctness
* consistency
* latency

---

## License

MIT License

---

## Citation

If you use this work:

```
Ponciano, J.-J. (2026). Reproducible LLM Workflows with Ollama.
```

---

## Final Insight

> The model is not the system.
> The workflow is the system.

```
