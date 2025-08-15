# RAG-Powered Blog Content Analyzer

A sophisticated Retrieval-Augmented Generation (RAG) system that intelligently extracts, processes, and queries blog content using advanced NLP techniques and OpenAI's language models.

## 🚀 Overview

This project demonstrates a complete RAG pipeline that scrapes web content, creates semantic embeddings, and enables natural language querying of blog posts. Built with LangChain and OpenAI, it showcases modern approaches to document retrieval and question-answering systems.

## ✨ Features

- **Intelligent Web Scraping**: Selective content extraction using BeautifulSoup with targeted parsing
- **Advanced Text Processing**: Recursive character-based text splitting with configurable chunk sizes and overlap
- **Semantic Search**: Vector embeddings using OpenAI's embedding models stored in Chroma vector database
- **RAG Implementation**: Context-aware question answering using retrieved relevant chunks
- **Streaming Responses**: Real-time token streaming for improved user experience
- **Modular Architecture**: Clean, extensible codebase following best practices

## 🛠️ Technology Stack

- **LangChain**: Framework for building LLM applications
- **OpenAI GPT-3.5-turbo**: Large language model for text generation
- **OpenAI Embeddings**: Text vectorization for semantic search
- **Chroma**: Vector database for storing and retrieving embeddings
- **BeautifulSoup**: Web scraping and HTML parsing
- **Python-dotenv**: Environment variable management

## 📋 Prerequisites

- Python 3.8+
- OpenAI API key
- Internet connection for web scraping

## 🔧 Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd RAGProject
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**
   
   Create a `.env` file in the project root:
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   ```

## 🚀 Usage

### Basic Usage

Run the main script with a default query:
```bash
python main.py
```

### Custom Queries

Modify the query in `main.py`:
```python
if __name__ == "__main__":
    query = "Your question here"
    for chunk in rag_chain.stream(query):
        print(chunk, end="", flush=True)
```

### Example Queries

- "What is maximum inner product search?"
- "Explain the main concepts discussed in the blog post"
- "What are the key takeaways from this article?"

## 📁 Project Structure

```
RAGProject/
├── main.py              # Main application script
├── requirements.txt     # Python dependencies
├── .env                # Environment variables (create this)
└── README.md           # Project documentation
```

## ⚙️ Configuration

### Text Splitting Parameters
```python
text_splitter = RecursiveCharacterTextSplitter(
    chunk_size=1000,        # Maximum characters per chunk
    chunk_overlap=200       # Overlap between chunks
)
```

### Target Website
Currently configured to scrape from:
- `https://lilianweng.github.io/posts/2023-06-23-agent/`

To change the target URL, modify the `web_paths` parameter in the `WebBaseLoader`.

### Content Targeting
The scraper focuses on specific HTML classes:
- `post-content`: Main article content
- `post-title`: Article title
- `post-header`: Header information

## 🔍 How It Works

1. **Content Loading**: WebBaseLoader fetches and parses the target blog post
2. **Text Chunking**: Content is split into overlapping chunks for optimal retrieval
3. **Vectorization**: Each chunk is converted to embeddings using OpenAI's embedding model
4. **Storage**: Embeddings are stored in a Chroma vector database
5. **Retrieval**: User queries are embedded and matched against stored chunks
6. **Generation**: Relevant chunks provide context for GPT-3.5-turbo to generate answers

## 📊 Performance Considerations

- **Chunk Size**: Balance between context and precision (default: 1000 characters)
- **Chunk Overlap**: Ensures continuity across chunks (default: 200 characters)
- **Retrieval Count**: Number of relevant chunks to retrieve (configurable in retriever)

## 🔒 Security Notes

- Store your OpenAI API key securely in the `.env` file
- Never commit API keys to version control
- Consider implementing rate limiting for production use
