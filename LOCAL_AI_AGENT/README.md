# Local AI Agent — Restaurant Review RAG System

A locally running AI application that answers natural-language questions about restaurant reviews using Retrieval-Augmented Generation (RAG). The system retrieves relevant reviews from a local vector database and uses a language model to generate context-aware responses.

## Overview

The Local AI Agent combines semantic search with a local language model to answer questions grounded in restaurant review data. Instead of relying entirely on a model's pretrained knowledge, it retrieves relevant information from a dataset before generating a response.

The application uses Ollama for local model execution and embeddings, LangChain to orchestrate the retrieval pipeline, and ChromaDB to store and search document embeddings.

## Features

- **Retrieval-Augmented Generation:** Retrieves relevant restaurant reviews before generating answers.
- **Semantic Search:** Finds reviews based on meaning rather than exact keyword matches.
- **Local Model Execution:** Uses Ollama to run the embedding model and language model locally.
- **Vector Database:** Stores restaurant review embeddings using ChromaDB.
- **Metadata Support:** Preserves review ratings and dates alongside document content.
- **Interactive Question Answering:** Allows users to ask questions through a command-line interface.
- **Persistent Storage:** Saves the vector database locally for reuse across application runs.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core application development |
| LangChain | RAG pipeline and component integration |
| Ollama | Local model execution and text embeddings |
| `mxbai-embed-large` | Text embedding generation |
| ChromaDB | Vector storage and similarity search |
| Pandas | Loading and processing CSV data |

## Architecture

The application follows a retrieval-augmented generation workflow:

1. **Data Ingestion:** Loads restaurant review records from a CSV file using Pandas.
2. **Document Preparation:** Converts each review into a LangChain document containing text and metadata.
3. **Embedding Generation:** Uses Ollama to convert document text into numerical vectors.
4. **Vector Storage:** Stores the embeddings and associated documents in ChromaDB.
5. **Query Processing:** Accepts a question from the user through the command-line interface.
6. **Relevant Document Retrieval:** Searches the vector database and retrieves the five most relevant reviews.
7. **Response Generation:** Passes the retrieved context and question to the language model to generate an answer.

## Project Structure

```text
LOCAL_AI_AGENT/
├── main.py
├── vector.py
├── realistic_restaurant_reviews.csv
├── requirements.txt
├── README.md
├── .gitignore
└── chroma_db/                 # Generated locally; excluded from Git
```

The `chroma_db/` directory is generated locally when the vector database is initialized. It should not be committed to the repository.

## Prerequisites

Before running the project, ensure you have:

- Python 3.10 or a compatible version supported by your installed dependencies
- Git
- Ollama installed and running
- The required Ollama embedding model downloaded
- A compatible local chat model configured in `main.py`

## Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/AdityaRoy26/GenAI-Projects.git
cd GenAI-Projects/LOCAL_AI_AGENT
```

If this project is stored in a separate GitHub repository, use that repository's URL and navigate to its root directory instead.

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate the environment on Windows:

```powershell
.\venv\Scripts\Activate.ps1
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Start Ollama

Install Ollama from the official website:

https://ollama.com/download

Make sure the Ollama application is running, then download the embedding model:

```bash
ollama pull mxbai-embed-large
```

The application also requires the chat model configured in `main.py`. Download that model using `ollama pull MODEL_NAME`, replacing `MODEL_NAME` with the model specified in your code.

### 5. Run the Application

From the project directory, execute:

```bash
python main.py
```

Enter a question when prompted. To exit the application, enter `q`.

## Example Usage

```text
Ask your question (q to quit): What do customers think about the food quality?

[The application retrieves relevant restaurant reviews and generates
a response based on the retrieved context.]
```

The exact response depends on the contents of the dataset, the retrieved reviews, and the configured language model.

## Configuration

### Embedding Model

The project uses the following embedding model in `vector.py`:

```python
OllamaEmbeddings(model="mxbai-embed-large")
```

### Retrieval Settings

The retriever is configured to return up to five relevant documents per query:

```python
retriever = vector_store.as_retriever(
    search_kwargs={"k": 5}
)
```

The number of retrieved documents can be adjusted depending on the dataset and the desired balance between context and response quality.

### Vector Database

ChromaDB stores the restaurant review documents and their embeddings in a local persistent directory. The database can be regenerated from the CSV dataset when necessary.

## Dataset

The project uses `realistic_restaurant_reviews.csv` as its source of restaurant review data.

Each record is processed into a document containing the review title and text, along with metadata such as rating and date.

Ensure you have permission to redistribute the dataset before publishing it in a public repository.

## Limitations

- Answer quality depends on the relevance and completeness of the retrieved reviews.
- The system may generate inaccurate information if the retrieved context is insufficient or the language model makes unsupported inferences.
- Local inference performance depends on the available hardware and the selected models.
- Initial database creation can take time because the documents must be embedded.
- The embedding model and chat model must be available through Ollama.

## Future Improvements

- Add a web interface using Streamlit or FastAPI.
- Support filtering by rating and review date.
- Display the source reviews used to generate each answer.
- Add document deduplication and more robust database initialization.
- Improve error handling and configuration management.
- Evaluate retrieval quality and answer faithfulness using a test dataset.

## Learning Outcomes

This project demonstrates practical implementation of:

- Retrieval-Augmented Generation (RAG)
- Text embeddings and semantic similarity search
- Vector database integration
- Document processing and metadata management
- Local Large Language Model (LLM) integration
- Building an interactive question-answering pipeline with LangChain

## Author

**Aditya Roy**

GitHub: [AdityaRoy26](https://github.com/AdityaRoy26)

## License

Add a license if you intend to distribute this project publicly. If the dataset has separate licensing or usage restrictions, follow those terms as well.
