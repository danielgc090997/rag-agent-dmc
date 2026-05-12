# Academic Chatbot with RAG (Retrieval-Augmented Generation)

An intelligent chatbot designed to answer questions about academic courses using document retrieval and generative AI. This project demonstrates a hybrid conversational AI system that combines intent classification, vector search, and LLM-powered responses.

## Features

- **Document Ingestion**: Loads and processes PDF documents from academic courses
- **Vector Search**: Uses FAISS and HuggingFace embeddings for efficient document retrieval
- **Intent Classification**: Keyword-based classifier to route between conversational and RAG modes
- **Memory Management**: Maintains conversation history for context-aware responses
- **Guardrails**: Built-in filters to prevent off-topic or inappropriate queries
- **Modular Design**: Clean separation of components for easy extension

## Architecture

The chatbot uses a two-path approach:
- **Conversational Path**: For greetings, small talk, and general queries
- **RAG Path**: For academic questions, retrieving relevant information from loaded documents

Key components:
- PDF loading with PyPDFLoader
- Text chunking with RecursiveCharacterTextSplitter
- Embeddings via HuggingFace (multilingual-e5-base)
- Vector storage with FAISS
- LLM: Google Gemini 2.5 Flash Lite
- Intent classifier with keyword matching
- Memory system for conversation history

## Technologies Used

- **Python 3.x**
- **LangChain**: For LLM integration and document processing
- **FAISS**: Vector database for similarity search
- **HuggingFace Transformers**: For embeddings
- **Google Generative AI**: LLM backend
- **Jupyter Notebook**: For development and demonstration

## Installation

1. Clone the repository:
```bash
git clone https://github.com/danielgc090997/rag-agent-dmc.git
cd rag-agent-dmc
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Set up environment variables:
Create a `.env` file with your Google API key:
```
GOOGLE_API_KEY=your_api_key_here
```

4. Place your PDF documents in the `datapdf/` directory

## Usage

1. Open the Jupyter notebook:
```bash
jupyter notebook notebooks/driver.ipynb
```

2. Run the cells in order to:
   - Load and process documents
   - Set up embeddings and vector store
   - Configure the LLM
   - Create the chatbot instance

3. Use the `preguntar()` function to interact with the chatbot:
```python
preguntar("What is the email of the programming course instructor?")
```

## Project Structure

```
agent-dmc/
├── datapdf/              # PDF documents for the knowledge base
├── notebooks/
│   └── driver.ipynb      # Main implementation notebook
├── requirements.txt      # Python dependencies
└── README.md            # This file
```

## Key Classes

- `ClasificadorIntencion`: Classifies user intent (conversational vs. academic)
- `ChatbotAcademico`: Main chatbot class with RAG and memory
- `MemoriaConversacional`: Conversation history management

## Guardrails

The system includes several safety measures:
- Keyword filtering to block jokes, gossip, and off-topic content
- Strict RAG prompts that only use provided context
- Intent routing to ensure appropriate response types

## Future Improvements

- Replace keyword classifier with ML-based intent detection
- Add support for more document formats
- Implement user authentication and session management
- Add evaluation metrics for response quality
- Deploy as a web application

## License

MIT License - feel free to use and modify for your own projects.

## Contributing

Contributions welcome! Please open issues for bugs or feature requests.