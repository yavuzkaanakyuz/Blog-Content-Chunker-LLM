# Blog-Content-Chunker-LLM

# Blog Content Chunker LLM

This project leverages web scraping and large language models (LLM) to load, chunk, and retrieve information from blog content. It scrapes and indexes the contents of a blog post, splits the content into manageable chunks, and uses OpenAI embeddings to enable efficient content retrieval.

## Key Features:
- Scrapes blog content using `BeautifulSoup` (bs4).
- Uses the LangChain framework for chunking and indexing content.
- Implements OpenAI embeddings for semantic search and retrieval.
- Answers questions related to the blog content using a RAG (Retrieval-Augmented Generation) approach with OpenAI's GPT-3.5-turbo.

## How It Works:
1. Web scraping: Fetches specific content sections from a blog post using `WebBaseLoader` and `BeautifulSoup`.
2. Content chunking: Splits the blog content into smaller, overlapping chunks for better indexing and retrieval.
3. Embeddings: Generates vector embeddings for the text chunks using `OpenAIEmbeddings` and stores them in a vector database (Chroma).
4. Question answering: Combines the retrieved chunks and provides answers to user questions using a fine-tuned prompt and OpenAI's LLM.

### How to Run:
- Clone this repository.
- Set up the necessary environment variables (load OpenAI API keys using `.env`).
- Run the script, and ask it a question related to the blog post content.

### Requirements:
- `bs4`
- `langchain`
- `langchain-chroma`
- `langchain-openai`
- `dotenv`


