# AI Chatbot Agent for Campus Queries

**MIT School of Computing**  
**MIT Art, Design and Technology University (MIT-ADT), Pune**  
**Department of Computer Science & Engineering**  
**Class: SY CSE 12 | Group ID: 1203**  
**Semester 1 PBL Project (A.Y. 2024-25)**  

**Developed by:** Vrushali Dhakane  
**Faculty Guide:** Prof. Pratik Kamble  

## Project Overview

This repository contains an **AI-powered campus query chatbot** designed specifically for students and faculty at MIT-ADT University. The system provides instant, accurate, and 24/7 answers to common campus-related questions, including:

- Class timetables and lecture schedules  
- Syllabus, handbooks, and notices (with direct PDF links)  
- Administrative information (admissions, fees, certificates)  
- Real-time professor cabin/office availability and location  

The chatbot uses **natural language understanding** to handle casual queries (e.g., "When is my ENT lecture tomorrow?", "Is Prof. XYZ in cabin today?", "Send syllabus PDF").

## Core Technology: Retrieval-Augmented Generation (RAG)

The chatbot is built using a **Retrieval-Augmented Generation (RAG)** architecture to ensure responses are factually grounded in official campus documents rather than relying solely on LLM parametric knowledge.

### RAG Pipeline

1. **Document Ingestion**  
   - Campus PDFs (timetables, syllabus, handbook, notices, professor schedules) are split into chunks  
   - Text is embedded using sentence-transformers (e.g., all-MiniLM-L6-v2)

2. **Vector Database**  
   - Embeddings stored in FAISS / Chroma for fast semantic search

3. **Retrieval**  
   - User query → embedded → top-k relevant chunks retrieved via cosine similarity

4. **Augmentation**  
   - Retrieved context injected into prompt with strict instructions:  
     - Answer only from provided documents  
     - Include direct links when PDFs/notices are referenced  
     - Handle unknown queries gracefully

5. **Generation**  
   - LLM generates natural, concise, and accurate responses (OpenAI GPT / Groq / open-source models)

## Features

- Natural language query support  
- Real-time professor availability checks  
- Direct clickable links to official PDFs/documents  
- 24/7 availability with low latency responses  
- Responsive chat interface with MIT-ADT branding

## Tech Stack

- **Language**: Python 3.10+  
- **RAG Framework**: LangChain / LlamaIndex  
- **Embeddings**: sentence-transformers  
- **Vector Store**: FAISS or Chroma  
- **LLM**: OpenAI API / Groq / Hugging Face models  
- **Frontend**: Streamlit / Flask / HTML + JavaScript  
- **Deployment**: Vercel / Render / Railway

## Problem Solved

Students waste significant time searching fragmented sources (notice boards, websites, emails, manual inquiries) for timetables, notices, and professor availability. This causes delays, missed meetings, frustration, and reduced productivity.

The RAG-powered chatbot eliminates these issues by delivering centralized, reliable, and instant answers grounded in official data.

## Scope (Semester 1 PBL)

- Focused on MIT School of Computing (CSE department)  
- Text-based queries only  
- Manual document upload/update (no live API sync in MVP)  
- Static professor availability data (future: calendar integration)

