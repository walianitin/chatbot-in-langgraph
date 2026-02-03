# Chatbot in LangGraph

A comprehensive collection of chatbot implementations built with LangGraph and Streamlit, showcasing various features like conversation memory, tool integration, RAG (Retrieval-Augmented Generation), and database persistence.

## 📋 Project Overview

This project demonstrates multiple chatbot implementations using LangGraph, a framework for building stateful, multi-actor applications with LLMs. Each implementation showcases different capabilities and features, from basic conversational AI to advanced RAG-enabled chatbots with custom tools.

## 🚀 Features

### Available Implementations

1. **Basic Chatbot** (`langgraph_backend.py` + `streamlit_frontend.py`)
   - Simple conversational chatbot with in-memory state management
   - OpenAI GPT integration
   - Basic conversation history

2. **Database-Backed Chatbot** (`langgraph_database_backend.py` + `streamlit_frontend_database.py`)
   - Persistent conversation storage using SQLite
   - Multiple thread management
   - Conversation history across sessions

3. **Tool-Enhanced Chatbot** (`langgraph_tool_backend.py` + `streamlit_frontend_tool.py`)
   - Integrated custom tools:
     - **DuckDuckGo Search**: Web search capabilities
     - **Stock Price Lookup**: Real-time stock prices via Alpha Vantage API
     - **Calculator**: Basic arithmetic operations (add, sub, mul, div)
   - Automatic tool selection and execution
   - Thread-based conversation persistence

4. **RAG-Enabled Chatbot** (`langraph_rag_backend.py` + `streamlit_rag_frontend.py`)
   - PDF document upload and processing
   - Vector-based document retrieval using FAISS
   - OpenAI embeddings for semantic search
   - Combined capabilities:
     - PDF question-answering
     - Web search
     - Stock prices
     - Calculator
   - Per-thread document storage

5. **Streaming Chatbot** (`streamlit_frontend_streaming.py`)
   - Real-time response streaming
   - Enhanced user experience with live updates

6. **Threading-Based Chatbot** (`streamlit_frontend_threading.py`)
   - Asynchronous processing
   - Improved performance for concurrent requests

7. **MCP (Model Context Protocol) Chatbot** (`langgraph_mcp_backend.py` + `streamlit_frontend_mcp.py`)
   - Advanced protocol integration
   - Extended context management

## 🛠️ Installation

### Prerequisites

- Python 3.8 or higher
- OpenAI API key (required)
- Alpha Vantage API key (optional, for stock price lookup feature)

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/walianitin/chatbot-in-langgraph.git
   cd chatbot-in-langgraph
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure environment variables**
   
   Create a `.env` file in the project root:
   ```bash
   OPENAI_API_KEY=your_openai_api_key_here
   # Optional: For stock price lookup feature
   # ALPHA_VANTAGE_API_KEY=your_alpha_vantage_api_key
   ```
   
   Note: The current implementation includes a demo Alpha Vantage API key in the code, but you should obtain your own key from [Alpha Vantage](https://www.alphavantage.co/support/#api-key) for production use.

## 💻 Usage

### Running the Basic Chatbot

```bash
streamlit run streamlit_frontend.py
```

### Running the Database-Backed Chatbot

```bash
streamlit run streamlit_frontend_database.py
```

### Running the Tool-Enhanced Chatbot

```bash
streamlit run streamlit_frontend_tool.py
```

### Running the RAG-Enabled Chatbot

```bash
streamlit run streamlit_rag_frontend.py
```

### Running the Streaming Chatbot

```bash
streamlit run streamlit_frontend_streaming.py
```

### Running the Threading Chatbot

```bash
streamlit run streamlit_frontend_threading.py
```

### Running the MCP Chatbot

```bash
streamlit run streamlit_frontend_mcp.py
```

## 📦 Key Dependencies

- **LangGraph**: Framework for building stateful LLM applications
- **LangChain**: Tools and utilities for LLM integration
- **Streamlit**: Web UI framework
- **OpenAI**: LLM provider
- **FAISS**: Vector similarity search (for RAG)
- **SQLite**: Persistent storage
- **DuckDuckGo Search**: Web search integration

## 🏗️ Architecture

Each chatbot implementation follows a similar architecture:

1. **Backend** (`langgraph_*_backend.py`):
   - Defines the state graph and nodes
   - Configures tools and LLM
   - Sets up checkpointers for conversation persistence
   - Compiles the chatbot graph

2. **Frontend** (`streamlit_*_frontend.py`):
   - Streamlit-based user interface
   - Chat input/output handling
   - Session state management
   - Integration with backend

### LangGraph State Graph

The chatbots use LangGraph's StateGraph to manage conversation flow:
- **States**: Track conversation messages and context
- **Nodes**: Process messages (LLM nodes, tool nodes)
- **Edges**: Define conversation flow
- **Checkpointers**: Save conversation state for persistence

## 🔧 Customization

### Adding New Tools

To add custom tools to the tool-enhanced or RAG chatbot:

1. Define your tool using the `@tool` decorator:
   ```python
   from langchain_core.tools import tool
   
   @tool
   def my_custom_tool(param: str) -> dict:
       """Tool description for the LLM"""
       # Your implementation
       return {"result": "value"}
   ```

2. Add the tool to the tools list:
   ```python
   tools = [search_tool, get_stock_price, calculator, my_custom_tool]
   ```

### Using Different LLMs

Change the LLM model in the backend files:
```python
llm = ChatOpenAI(model="gpt-4")  # or gpt-3.5-turbo, etc.
```

## 🤝 Contributing

Contributions are welcome! Feel free to submit issues or pull requests.

## 📄 License

This project is open source and available under the MIT License.

## 🙏 Acknowledgments

- Built with [LangGraph](https://github.com/langchain-ai/langgraph)
- UI powered by [Streamlit](https://streamlit.io/)
- LLM integration via [LangChain](https://github.com/langchain-ai/langchain)

## 📞 Contact

For questions or feedback, please open an issue on GitHub.
