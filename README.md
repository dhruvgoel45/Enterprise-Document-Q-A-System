
# Enterprise Document Q&A System (RAG) with Multi-Modal Input :dart:

This project is an **Enterprise Document Q&A System** designed for **Retrieval-Augmented Generation (RAG)** with support for multi-modal inputs. It can ingest various document formats, such as **PDFs, spreadsheets, and emails**, and allows users to query the content using natural language. The system processes **text, images, and structured data (tables)**, providing accurate answers with references to the specific sections of the document. Powered by **Large Language Models (LLM)**, it integrates multiple inputs for a richer and more insightful user experience.

## Prerequisites

* Python >= 3.10
* **Poetry** ([Install Guide](https://python-poetry.org/docs/))

#### Large Language Models (LLMs)
* To use OpenAI models, you need a valid key. Generate one [here](https://platform.openai.com/api-key).
* For local LLM models, install **Ollama**. Follow the installation instructions [here](https://ollama.ai/download).

#### Ollama
To set up a local LLM, you can download the `orca2` model (set by default in `settings.toml`). To download and run the model:

```bash
ollama run orca2
```

#### Databases
* To use **Elasticsearch**, ensure a running cluster or use a test deployment via the [docker-es.sh](./scripts/docker-es.sh) script.

## Installation

Clone the repository and install the necessary dependencies using **Poetry**:

```bash
git clone https://github.com/yourusername/enterprise-document-qa-system.git
cd enterprise-document-qa-system
poetry install # -E audio -E image
```

* The `audio` extra installs **openai-whisper** for speech-to-text.
* The `image` extra installs **transformers** and **pillow** for image captioning.

> **Note**: Certain libraries used in this project may not run on Windows. It is highly recommended to use a **Linux** environment for smooth execution.

## Usage - Server

1. Modify the `settings.toml` file as needed.
2. Start the server by running:

```bash
poetry run python exact_rag/main.py
```

> The first startup may take a while to download the models, especially for image captioning.

## Usage - UI (Demo)

The demo UI is built with **Streamlit**. To quickly try the features locally, ensure the `dev` dependencies are installed, then run:

```bash
poetry run streamlit run frontend/ui.py
```

## Example Use Cases

Find usage examples in the [examples](./examples/) folder. Here are two notable cases:

1. **Chat with Images**: Demonstrates querying documents with embedded images.
2. **Chat with PDFs and Tables**: Shows interactions with documents containing both unstructured text and structured tables.

## Running Tests

To execute tests, ensure `dev` dependencies are installed:

```bash
poetry install --with-dev # -E audio -E image
```

Run tests with:

```bash
poetry run pytest tests/
```

---

