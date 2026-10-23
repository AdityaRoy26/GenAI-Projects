# GenAI Projects

A collection of hands-on projects, experiments, and learning resources focused on Generative AI, Large Language Models (LLMs), LangChain, Retrieval-Augmented Generation (RAG), and AI-powered applications.

This repository documents my practical learning journey in Generative AI, from experimenting with LangChain and prompts to building local AI applications.

## Repository Overview

The repository is organized into separate folders so that each project or learning area can be explored independently.

| Directory / File | Description |
|---|---|
| `LOCAL_AI_AGENT/` | A local restaurant-review question-answering application built with Retrieval-Augmented Generation (RAG), LangChain, ChromaDB, and Ollama. |
| `langchain/` | LangChain experiments and learning examples. |
| `LANGCHAIN PROMPTS/` | Prompt examples and experiments for working with language models. |
| `main.py` | Python entry-point or experiment file at the repository root. Review the code before running it to understand its purpose and configuration. |

The contents of the repository may evolve as new projects and experiments are added.

## Featured Project: Local AI Agent

The `LOCAL_AI_AGENT/` project answers natural-language questions about restaurant reviews using a local retrieval-augmented generation pipeline.

### Key components

- **Python** for application logic
- **LangChain** for connecting retrieval and language-model components
- **Ollama** for local model execution and embeddings
- **ChromaDB** for persistent vector storage and semantic search
- **Pandas** for loading and preparing the review dataset

### How it works

1. Loads restaurant review records from a CSV file.
2. Converts review text into documents with associated metadata.
3. Generates embeddings using the configured Ollama embedding model.
4. Stores documents and embeddings in ChromaDB.
5. Retrieves relevant reviews for a user's question.
6. Uses the configured language model to produce a context-aware answer.

For project-specific dependencies and instructions, see [`LOCAL_AI_AGENT/README.md`](LOCAL_AI_AGENT/README.md).

## Getting Started

### Prerequisites

Requirements vary by project. Depending on which folder you want to run, you may need:

- Python 3.10 or a compatible version for the project's dependencies
- Git
- The packages listed in that project's `requirements.txt`, if provided
- Ollama and the required local models for `LOCAL_AI_AGENT/`

### Clone the repository

```bash
git clone https://github.com/AdityaRoy26/GenAI-Projects.git
cd GenAI-Projects
```

### Explore a project

Open the folder you want to work with and read its project-specific instructions before running the code. If a folder has its own `README.md` or `requirements.txt`, use those files as the source of truth for setup.

For Python projects, it is recommended to create a separate virtual environment for each project:

```bash
python -m venv .venv
```

On Windows PowerShell, activate it with:

```powershell
.\.venv\Scripts\Activate.ps1
```

Install dependencies only after navigating to the relevant project folder and checking whether it provides a `requirements.txt`:

```bash
pip install -r requirements.txt
```

## Repository Guidelines

- Keep each project in its own directory where practical.
- Add a project-level `README.md` with setup instructions, dependencies, and usage examples.
- Keep generated files, virtual environments, model caches, and local vector databases out of version control.
- Store secrets and API keys in environment variables or a local `.env` file; never commit credentials.
- Include a `.env.example` file when a project needs environment variables, using placeholder values only.
- Include dataset attribution and licensing information when applicable.
- Prefer reproducible setup steps so projects can be run on another machine.

## Security and Files to Exclude

Do not commit local environment files or generated artifacts, including:

```gitignore
.env
.env.*
!.env.example
venv/
.venv/
__pycache__/
*.py[cod]
chroma_db/
chroma.sqlite3
.ipynb_checkpoints/
```

Review the repository's `.gitignore` before pushing changes. If a secret has already been committed or pushed, revoke or rotate it; adding it to `.gitignore` alone does not remove it from Git history.

## Learning Goals

This repository is intended to build practical experience with:

- Prompt engineering
- LangChain components and workflows
- Large Language Model integration
- Text embeddings and semantic search
- Vector databases
- Retrieval-Augmented Generation (RAG)
- Building and debugging local AI applications

## Future Improvements

Planned improvements may include:

- Adding more standalone GenAI projects
- Documenting setup and execution steps for each project
- Adding screenshots or demonstrations where useful
- Improving configuration and error handling
- Exploring more advanced RAG pipelines and AI-agent workflows

## Author

**Aditya Roy**

GitHub: [AdityaRoy26](https://github.com/AdityaRoy26)

## License

Unless a license file is present, no reuse license is implied. Check the license and terms for each included project, dependency, and dataset before redistributing them.
