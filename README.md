# HAT (Hybrid Autonomous Tool) Project

## Overview
HAT is an advanced question-answering system that combines the power of vector stores and Wikipedia search to provide accurate and contextual responses. The system intelligently routes questions to the most appropriate data source using a sophisticated routing mechanism.

## Features
- **Smart Question Routing**: Automatically determines whether to use vector store or Wikipedia search based on the question context
- **Vector Store Integration**: Efficiently stores and retrieves document embeddings using Cassandra
- **Wikipedia Integration**: Seamless access to Wikipedia's vast knowledge base
- **Hybrid Search**: Combines multiple data sources for comprehensive answers
- **Scalable Architecture**: Built using LangGraph for efficient workflow management

## Technical Architecture
- **Vector Store**: Cassandra with HuggingFace embeddings
- **LLM**: Groq for text generation and routing
- **Graph Framework**: LangGraph for workflow orchestration
- **Embeddings**: HuggingFace's all-MiniLM-L6-v2 model
- **External APIs**: Wikipedia and ArXiv integration

## Setup and Installation

### Prerequisites
```bash
pip install langchain langgraph cassio
pip install langchain_community
pip install -U langchain_community tiktoken langchain-groq langchainhub chromadb langchain langgraph langchain_huggingface
pip install arxiv wikipedia
```

### Environment Variables
Set up the following environment variables:
```bash
ASTRA_DB_APPLICATION_TOKEN="your_token"
ASTRA_DB_ID="your_db_id"
GROQ_API_KEY="your_groq_api_key"
```

## Usage

### Basic Example
```python
# Initialize the system
inputs = {
    "question": "What is an agent?"
}

# Get response
for output in app.stream(inputs):
    for key, value in output.items():
        print(f"Node '{key}':")
    print("\n---\n")
```

## Components

### 1. Router
- Routes questions to appropriate data source
- Uses structured output for decision making
- Supports vectorstore and wiki_search options

### 2. Vector Store
- Stores document embeddings
- Handles similarity search
- Manages document retrieval

### 3. Wikipedia Search
- Integrates with Wikipedia API
- Provides access to general knowledge
- Handles non-specialized queries

## Graph Structure
```
START
  ├── route_question
  │   ├── wiki_search
  │   └── vectorstore
  └── END
```

## Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments
- LangChain team for the core framework
- Cassandra team for vector store support
- HuggingFace for embeddings model
