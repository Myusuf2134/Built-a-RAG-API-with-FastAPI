# 🤖 RAG API Project: AI-Powered Question Answering with FastAPI

## Overview

This project is a **hands-on implementation of a Retrieval-Augmented Generation (RAG) API**, designed to simulate how modern AI systems combine **search + generation** to answer questions accurately.

It helped me practice:

- Building an API using FastAPI  
- Creating and storing embeddings with Chroma (vector database)  
- Running a local LLM using Ollama (TinyLlama)  
- Designing a query endpoint (`/query`) for real-time AI responses  
- Understanding how RAG pipelines work end-to-end  
- Testing APIs using Swagger UI and curl  
- Debugging how data flows between embeddings → retrieval → LLM  

The goal was to **simulate a real-world AI backend system** similar to what powers chatbots, internal knowledge assistants, and AI search tools.

---

## 🧠 Architecture / How It Works

**Flow of Data:**

1. User sends a question to `/query`  
2. The question is converted into embeddings  
3. Chroma compares it with stored document embeddings  
4. Relevant documents are retrieved  
5. Context + question are sent to the LLM (TinyLlama via Ollama)  
6. The LLM generates a final response  
7. API returns the answer  

---

## 🔧 How I Built It

### Step 1: Environment Setup

1. Set up Python virtual environment  
2. Installed dependencies:
   - FastAPI  
   - Uvicorn  
   - ChromaDB  
3. Installed Ollama to run local LLMs  
4. Pulled the TinyLlama model for lightweight testing  

> Using a local LLM removes dependency on external APIs and simulates real production-like AI systems.

---

### Step 2: Creating the Knowledge Base

1. Created text documents (e.g., “What is Kubernetes”)  
2. Stored them as the project’s knowledge base  
3. Generated embeddings for each document  
4. Stored embeddings in Chroma vector database  

> This step helped me understand how raw text becomes searchable using embeddings instead of keywords.

---

### Step 3: Building the RAG Pipeline

1. Converted incoming user queries into embeddings  
2. Queried Chroma to find the most relevant documents  
3. Passed retrieved context into the LLM  
4. Used prompt engineering to generate clear, concise answers  

> The biggest insight here was learning how retrieval improves LLM accuracy by grounding responses in real data.

---

### Step 4: Creating the API

1. Built API using FastAPI  
2. Created a POST endpoint:
3. Accepted user input (`q=question`)  
4. Returned AI-generated response  

> Understanding how FastAPI handles routing and request/response cycles was a key learning moment.

---

### Step 5: Running and Testing

1. Ran the server using Uvicorn  
2. Tested API using:
   - curl (command line)  
   - Swagger UI (`/docs`)  

Example request:

```bash
curl -X POST "http://127.0.0.1:8000/query" \
--data-urlencode "q=What is Kubernetes?"
