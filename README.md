RAG API Project: AI-Powered Question Answering with FastAPI
Overview

This project is a hands-on implementation of a Retrieval-Augmented Generation (RAG) API, designed to simulate how modern AI systems combine search + generation to answer questions accurately.

It helped me practice:

Building an API using FastAPI

Creating and storing embeddings with Chroma (vector database)

Running a local LLM using Ollama (TinyLlama)

Designing a query endpoint (/query) for real-time AI responses

Understanding how RAG pipelines work end-to-end

Testing APIs using Swagger UI and curl

Debugging how data flows between embeddings → retrieval → LLM

The goal was to simulate a real-world AI backend system similar to what powers tools like chatbots, internal knowledge assistants, and AI search engines.

🧠 Architecture / How It Works

Flow of Data:

User sends a question to /query

The question is converted into embeddings

Chroma compares it with stored document embeddings

Relevant documents are retrieved

Context + question are sent to the LLM (TinyLlama via Ollama)

The LLM generates a final response

API returns the answer

🔧 How I Built It
Step 1: Environment Setup

Set up Python virtual environment

Installed dependencies:

FastAPI

Uvicorn

ChromaDB

Installed Ollama to run local LLMs

Pulled the TinyLlama model for lightweight testing

Using a local LLM was important because it removes dependency on external APIs and simulates real offline AI systems.

Step 2: Creating the Knowledge Base

Created text documents (e.g., “What is Kubernetes”)

Stored them as the project’s knowledge base

Generated embeddings for each document

Stored embeddings in Chroma vector database

This step helped me understand how raw text becomes searchable using embeddings instead of keywords.

Step 3: Building the RAG Pipeline

Converted incoming user queries into embeddings

Queried Chroma to find the most relevant documents

Passed retrieved context into the LLM

Used prompt engineering to ensure:

Clear

Concise answers

The biggest insight here was learning how retrieval improves LLM accuracy by grounding responses in real data.

Step 4: Creating the API

Built API using FastAPI

Created a POST endpoint:

/query

Accepted user input (q=question)

Returned AI-generated response

Understanding how FastAPI handles routing and request/response cycles was a key learning moment.

Step 5: Running and Testing

Ran the server using Uvicorn

Tested API using:

curl (command line)

Swagger UI (/docs)

Example request:

curl -X POST "http://127.0.0.1:8000/query" \
--data-urlencode "q=What is Kubernetes?"

Swagger UI made debugging much easier since I could test endpoints without writing extra code.

🚧 Challenges & Debugging

Understanding how FastAPI abstracts routing

Figuring out how embeddings connect to retrieval

Debugging incorrect or irrelevant responses from the LLM

Learning how context affects answer quality

The hardest part was connecting all components (API + vector DB + LLM). Once it clicked, the whole system made sense.

🎯 Key Takeaways

RAG is much more powerful than plain LLM prompting

Embeddings enable semantic search instead of keyword search

APIs are the backbone of production AI systems

Local LLMs (via Ollama) are great for learning and prototyping

🚀 Future Improvements

Add Docker containerization

Improve prompt engineering for better responses

Expand knowledge base with more documents

Add authentication and rate limiting

Deploy API to cloud (AWS/GCP)

📌 Why This Project Matters

This project reflects how real-world systems are built:

AI assistants

Internal company knowledge bots

DevOps documentation search tools

It demonstrates my ability to:

Build backend systems

Work with AI pipelines

Debug complex workflows

Think like an engineer, not just write code
