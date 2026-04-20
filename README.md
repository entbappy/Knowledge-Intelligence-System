# Knowledge Intelligence System

![Python](https://img.shields.io/badge/python-3.11+-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-experimental-orange)
![LLM](https://img.shields.io/badge/llm-OpenAI-lightgrey)

A lightweight document intelligence system that ingests text and PDF files, stores them in a Chroma vector store, uploads originals to S3-compatible storage, and answers questions using OpenAI conversational retrieval.

## Table of Contents

- [Features](#features)
- [Architecture](#architecture)
- [Project Structure](#project-structure)
- [Requirements](#requirements)
- [Installation](#installation)
- [Running the App](#running-the-app)
- [Configuration](#configuration)
- [Documentation](#documentation)
- [Workflows](#workflows)
- [License](#license)

## Features

- Upload `.txt` and `.pdf` documents through a Flask web UI
- Automatic text extraction and chunking
- Persistent semantic similarity search using Chroma vector store
- Conversational retrieval powered by OpenAI ChatGPT (`gpt-3.5-turbo`)
- File upload and storage via AWS S3-compatible service
- Clean separation of application components for easy extension

## Architecture

![Project Architecture](Assets/erwtfswfsdf%20(1).png)

This repository uses a modular design with:

- `app/main.py` — Flask web server, upload and query endpoints
- `app/models/vector_store.py` — Chroma vector store integration
- `app/services/llm_service.py` — conversational retrieval chain and memory
- `app/services/storage_service.py` — object storage upload/download
- `app/config.py` — environment-driven configuration

## Project Structure

```text
.
├── Assets/                         # Project screenshots and diagrams
├── app/                            # Core Flask application
│   ├── config.py                   # Environment and configuration
│   ├── main.py                     # Web server + upload/query endpoints
│   ├── models/                     # Persistence layer for vector search
│   └── services/                   # External service integrations
├── all-utils/                      # Utility notebooks and helpers
├── data/                           # Raw input or sample data
├── demo/                           # Drafts and design notes
├── docs/                           # Project documentation files
├── workflows/                      # Mermaid workflows for components
├── requirements.txt                # Python dependencies
├── README.md                       # This documentation
└── LICENSE                         # License file
```

## Requirements

- Python 3.11+
- `conda` (recommended) or any Python virtual environment
- OpenAI API credentials
- AWS credentials for S3 upload

## Installation

### Option A: Recommended Conda setup

```bash
conda create -n llmapp python=3.11 -y
conda activate llmapp
pip install -r requirements.txt
```

### Option B: Optional UV package manager (faster)

If you prefer a faster dependency installer, `uv` can be used as an alternative:

```bash
pip install uv
uv install -r requirements.txt
```

> `uv` is optional and may speed up installation on systems where it is available.

## Running the App

Create a `.env` file with the required environment variables, then launch the Flask app.

```bash
python app/main.py
```

Or, if you installed `uv` and want to use it for launching:

```bash
uv run python app/main.py
```

The application will start on `http://0.0.0.0:8080`.

## Configuration

Create a `.env` file in the project root with:

```env
OPENAI_API_KEY=your_openai_api_key
AWS_ACCESS_KEY=your_aws_access_key
AWS_SECRET_KEY=your_aws_secret_key
AWS_BUCKET_NAME=your_bucket_name
```

## Documentation

Detailed project documentation is available in the `docs/` folder:

- `docs/project_documentation.md`

## Workflows

Component workflow diagrams are available in the `workflows/` folder. The current files include:

- `workflows/full_system_architecture.md`
- `workflows/app_component.md`
- `workflows/vector_store_component.md`
- `workflows/llm_service_component.md`
- `workflows/storage_service_component.md`

## License

This project is licensed under the MIT License.
