# MediQuery-AI
# Local Healthcare RAG Assistant

Private, offline medical information assistant using **retrieval-augmented generation (RAG)**  
powered by **n8n** + **Ollama** + **Qdrant** — answers strictly from uploaded official medical documents.

**⚠️ Important legal & ethical notice**  
This is an **experimental/research tool only**.  
It is **not** a medical device, not certified, and **must not** be used for diagnosis, treatment decisions or patient care.  
Always verify every piece of information with original sources and qualified healthcare professionals.  
Use at your own risk.

## Features

- 100% local & offline (after initial model download)
- Upload Indian/international medical guidelines, protocols, SOPs (PDFs)
- Automatic chunking + embedding with local model
- Vector storage & semantic search in Qdrant
- Strict refusal when answer is not supported by documents
- Source citation (document name + section when metadata available)
- Simple chat interface inside n8n
- Optional public access via ngrok / Cloudflare Tunnel

## Technology Stack

| Component          | Tool                     | Runs on          |
|--------------------|--------------------------|------------------|
| Workflow & UI      | n8n                      | Docker           |
| LLM & Embeddings   | Ollama                   | Host machine     |
| Embedding model    | mxbai-embed-large        | Ollama           |
| Generation model   | Mistral / Llama 3.2 / …  | Ollama           |
| Vector database    | Qdrant                   | Docker           |
| Tunneling (opt.)   | ngrok / Cloudflare Tunnel| Docker / host    |

## Quick Start (Windows / Docker Desktop)

### 1. Prerequisites

- Docker Desktop running
- Ollama installed on host → https://ollama.com
- Pull models:

```bash
ollama pull mxbai-embed-large
ollama pull llama3.2:3b    # or mistral, llama3.1:8b, qwen2.5:7b, etc.
