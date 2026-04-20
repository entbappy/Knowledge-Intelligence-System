# Project Documentation

## Overview

The Knowledge Intelligence System is a Python-based project designed to build a searchable, conversational knowledge base from text and PDF documents. It uses OpenAI embeddings and Chroma to create a semantic vector store, while file uploads are saved to S3-compatible storage.

## Components

- `app/main.py` — Flask application with routes for upload and query.
- `app/models/vector_store.py` — Chroma vector store initialization and document indexing.
- `app/services/llm_service.py` — OpenAI chat model and conversational retrieval chain.
- `app/services/storage_service.py` — AWS S3-compatible upload/download interface.
- `app/config.py` — Environment variable configuration.

## How it works

1. User uploads a `.txt` or `.pdf` file via the web UI.
2. The document is temporarily saved and loaded using LangChain loaders.
3. Content is split into overlapping chunks.
4. Chunks are added to the Chroma vector store.
5. The original file is uploaded to object storage.
6. Users submit natural-language questions to query the knowledge base.
7. The LLM uses similarity search and prior chat state to return an answer.

## Usage

### Setup

1. Create a Python 3.11 environment.
2. Install dependencies using `pip`, or optionally `uv`.
3. Configure `.env` with OpenAI and AWS credentials.

### Running

- Start the Flask app with `python app/main.py`.
- Open the browser at `http://0.0.0.0:8080`.

## Project Notes

- Only `.txt` and `.pdf` files are currently supported.
- The vector store is persisted under `vector_db`.
- The S3 upload uses credentials from the `.env` file.
- The default LLM is `gpt-3.5-turbo`.

## Extending the Project

- Add support for more file formats in `app/main.py`
- Add additional retrieval logic in `app/services/llm_service.py`
- Swap the storage backend or add local storage support
- Add authentication and multi-user support for the web UI
- Add monitoring and metrics for upload/query performance
