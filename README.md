# Semantic-Search-with-ChromaDB
This Repository contains the Semantic Search flow , from visualization to semantic search....

# Semantic Search with ChromaDB

A lightweight semantic search engine that finds documents by meaning rather than exact keywords. Text is converted into vector embeddings, stored in ChromaDB, and retrieved using similarity search.

Example: searching for "how to fix a slow laptop" can return a document titled "Speeding up your computer's performance", even though they share almost no keywords.

# Features

Semantic (meaning-based) search over your own documents
Persistent vector storage with ChromaDB
Pluggable embedding models (default: all-MiniLM-L6-v2 via Sentence Transformers)
Metadata filtering (e.g. by category, source, or date)
Simple CLI / script interface for indexing and querying
Easy to extend into a RAG pipeline

# How It Works:

Documents ──► Chunking ──► Embedding model ──► ChromaDB (vector store)
                                                     ▲
User query ──► Embedding model ──► Similarity search ┘ ──► Top-K results

Ingest: documents are cleaned and split into chunks.
Embed: each chunk is converted into a dense vector.
Store: vectors, text, and metadata are saved in a ChromaDB collection.
Query: the query is embedded and compared to stored vectors using cosine similarity.
Return: the top-K most relevant chunks are returned with their scores.

# Tech Stack
Component	Tool
Vector database	ChromaDB
Embeddings	Sentence Transformers
Language	Python 3.9+

# Project Structure:
.
├── data/                # Raw documents (txt, csv, json, etc.)
├── chroma_db/           # Persisted ChromaDB data (auto-created)
├── src/
│   ├── ingest.py        # Load, chunk, embed, and store documents
│   ├── search.py        # Query the collection
│   └── utils.py         # Helper functions
├── requirements.txt
└── README.md
