Medical Chatbot - RAG-based Healthcare Assistant
An end-to-end medical question-answering chatbot using Retrieval-Augmented Generation (RAG), built with LangChain, Pinecone vector database, and deployed on AWS.
What It Does
This chatbot answers medical questions by retrieving relevant information from medical textbooks (PDFs) and generating accurate responses using a Large Language Model. Instead of fine-tuning an expensive model, it uses RAG to dynamically connect domain-specific medical knowledge with LLM intelligence.
Tech Stack

LLM: GPT-4 / Llama (via LangChain)
Vector Database: Pinecone (for embedding storage and similarity search)
Embeddings: SentenceTransformer (Hugging Face)
Framework: LangChain (for orchestration and prompt management)
Backend: Flask (Python web framework)
Deployment: AWS (with CI/CD pipeline)
Data Processing: PyPDF for text extraction, text chunking for token limits

How It Works

Data Ingestion: Medical PDF books are loaded and split into chunks (to fit LLM context window)
Embedding Creation: Text chunks are converted to vector embeddings using open-source models
Vector Storage: Embeddings are stored in Pinecone for fast similarity search
Query Processing: User question → similarity search in Pinecone → retrieve relevant chunks
Response Generation: Retrieved chunks + user query → LLM generates contextualized answer
Project Structure
medical-chat-bot/
├── data/              # Medical PDFs and source documents
├── research/          # Jupyter notebooks for experimentation
├── src/               # Modularized production code
│   ├── helper.py      # Utility functions
│   └── prompt.py      # Prompt templates
├── app.py             # Flask application (main entry point)
├── requirements.txt   # Python dependencies with pinned versions
├── setup.py           # Package configuration
└── .env               # API keys (Pinecone, OpenAI)
Setup Instructions
Prerequisites

Python 3.8+
Pinecone API key
OpenAI API key (or Hugging Face for open-source LLMs)

Installation
bash# Clone repository
git clone https://github.com/kcashmit0/medical-chat-bot.git
cd medical-chat-bot

# Create virtual environment
conda create -n medchatbot python=3.8 -y
conda activate medchatbot

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
# Create .env file with:
# PINECONE_API_KEY=your_key_here
# OPENAI_API_KEY=your_key_here
Running the Application
bashpython app.py
Why RAG Instead of Fine-Tuning?

Cost-effective: No expensive GPU training required
Dynamic updates: Add new medical knowledge without retraining
Domain-specific: Retrieves exact passages from medical textbooks
Scalable: Easy to expand knowledge base
Learning Goals
Building practical skills in:

Retrieval-Augmented Generation (RAG) architecture
Vector databases and similarity search
LangChain framework for LLM applications
Production-ready Python development
Cloud deployment with AWS

Acknowledgments
Based on end-to-end LLM project tutorial focusing on healthcare applications.

Notes
This is an educational project built while learning modern LLM application development. The chatbot is designed to demonstrate RAG architecture and should not be used for actual medical advice.