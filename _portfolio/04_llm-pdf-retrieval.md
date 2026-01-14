---
title: "LLM-Powered PDF Retrieval"
excerpt: "Using Mistral, LangChain, and RAG to turn PDFs into structured data."
collection: portfolio
permalink: /projects/llm-pdf-retrieval/
---

> Experimental tooling for extracting structured information from academic PDFs using Large Language Models. Built for learning and prototyping—**not** for production or compliance-critical workflows.

## Project at a Glance

In this project I built a small, focused pipeline that reads one or more research papers in PDF format and automatically produces a structured JSON summary for each file. Under the hood it combines:

- Lightweight **RAG-style retrieval** over PDF pages
- A **Mistral** LLM for reasoning and generation
- **LangChain** utilities for embedding, search, and document loading
- **Pydantic** models to strictly define the shape of the output

The result is a command-line tool that turns messy PDFs into consistent, machine-readable records.

## What the Tool Does

Given a folder of PDFs, the script:

1. Loads each PDF and splits it into pages.
2. Builds an in-memory vector store of page embeddings.
3. Retrieves the most relevant pages for a guiding question (e.g., “What is this paper about?”).
4. Feeds that condensed context into a Mistral model.
5. Parses the LLM’s response into a structured Pydantic model.
6. Saves all results into a single `output.json` file, one entry per PDF.

This setup makes it easy to batch‑process a corpus of papers and quickly see the most important fields in a unified format.

## Schema and Structured Output

A key part of the project is the strict schema enforced with Pydantic. The model captures fields such as:

- **Title:** inferred or extracted paper title.
- **Religion / Country:** domain-specific metadata for the papers I was exploring.
- **Key results and methodology:** short, human-readable summaries of the study.
- **Sample size and page count:** basic study and document stats.

Because the LLM output is validated against this schema, mistakes or missing fields are easier to spot and handle.

## Retrieval & LLM Stack

- **Document loading:** `PyPDFLoader` reads and splits PDFs into individual pages.
- **Embeddings:** `OllamaEmbeddings` convert each page into a vector representation.
- **Vector store:** `DocArrayInMemorySearch` indexes the pages for fast similarity search.
- **Retriever:** a simple retriever pulls the most relevant pages for the question prompt.
- **LLM:** a Mistral model (configured via API key) generates the structured answer.
- **Parsing:** `instructor` + Pydantic ensure the LLM output matches the expected structure.

This mirrors a modern RAG pattern, but in a compact, reproducible script.

## Configuration and Usage

The behavior of the tool is controlled via `config.py`:

- `INPUT_PATH`: folder where input PDFs are stored.  
- `OUTPUT_PATH`: folder where `output.json` will be written.  
- `MODEL_NAME`: which Mistral model to call.  
- `PARSER_USAGE`: flag to enable or disable the structured parser.

After configuring these values and your `MISTRAL_API_KEY`, you can run the script to process all PDFs in the input directory and inspect the resulting JSON.

## What I Focused On

- Exploring how to **combine RAG and LLMs** for semi‑structured academic PDFs.  
- Designing a **clean, typed interface** using Pydantic models instead of ad‑hoc JSON.  
- Keeping the pipeline small and understandable so it’s easy to extend with new fields, different questions, or alternative models.

## Tech Stack

- **Python**  
- **LangChain** (document loaders, vector store, retriever)  
- **Ollama embeddings** for local vectorization  
- **Mistral API** for LLM responses  
- **Pydantic** and **instructor** for structured outputs  

## Explore the Code

You can find the complete implementation and setup instructions here:

- GitHub repository: [carobs9/llm-pdf-retrieval](https://github.com/carobs9/llm-pdf-retrieval)

This portfolio entry highlights the core ideas; the README and code in the repo go deeper into configuration and running the tool locally.
