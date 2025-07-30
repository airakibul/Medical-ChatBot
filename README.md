# Medical-ChatBot

A smart medical chatbot powered by LangChain, OpenRouter, and modern NLP techniques that allows users to ask questions based on PDF medical documents. It processes PDF files, retrieves relevant context using vector search, and answers user queries in a concise manner using GPT-4o via OpenRouter.

---

## 🚀 Features

- 📚 Loads medical PDFs from the `data/` folder  
- 🧠 Answers questions using document content  
- 🔍 Retrieves relevant info via vector search (Pinecone)  
- ✂️ Splits text into chunks for efficient retrieval  
- 🤖 Uses GPT-4o via OpenRouter for response generation  
- ⚙️ RAG pipeline with LangChain  
- 🧠 Embeddings via HuggingFace (`all-MiniLM-L6-v2`)  
- 💬 Simple Flask-based chat interface  
- 🔐 Secure API key handling with `.env`  


---

## 🛠️ Technology Stack

- **Framework**: LangChain  
- **Interface**: Flask  
- **Embeddings**: HuggingFace (`sentence-transformers/all-MiniLM-L6-v2`)  
- **Vector Store**: Pinecone  
- **PDF Processing**: LangChain (`DirectoryLoader`, `PyPDFLoader`)  
- **Text Splitting**: `RecursiveCharacterTextSplitter`  
- **Retrieval-Augmented Generation**: LangChain RAG pipeline  
- **LLM**: GPT-4o via OpenRouter  
- **Environment Management**: `.env` with `python-dotenv`  


---

## 📋 Prerequisites

- Python 3.10+  
- An OpenRouter API key – [Get one here](https://openrouter.ai/)  
- A Pinecone API key – [Sign up at Pinecone](https://www.pinecone.io/)  
- A Pinecone index (e.g., `medical-bot`) must be created or will be created by the app  
- A `data/` folder containing one or more `.pdf` files  

---

## ⚙️ Installation

1. Clone the Repository

```bash
git clone https://github.com/airakibul/Medical-ChatBot.git

```

2. Create an environment

```bash
conda create -n interview python=3.10 -y

```
```bash
conda activate medibot

```

3. Create a .env file in the root directory and add your Pinecone & openai credentials as follows:

```bash

OPENROUTER_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
PINECONE_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

```

4. install requirements

```bash

pip install -r requirements.txt

```

---

5. run the following command to store embeddings to pinecone

```bash

python store_index.py

```

## Usage

1. Start the application

```bash

python app.py

```

2. open a browser and go to http://localhost:8080/
3. Start conversation with Chatbot

---

## Project Structure

```text
├── data
├── Research
│   └── trails.ipynb
├── src
│   ├── __init__.py
│   ├── helper.py
│   └── prompt.py
├── templates
│   └── index.html
├── static
│   └── style.css
├── app.py
├── store_index.py
├── setup.py
└── requirements.txt
```
---

## 📌 Features in Detail

- 📚 **PDF-Based Knowledge Base**: 
  The app automatically loads and processes medical PDF documents placed in the `data/` folder using LangChain's `DirectoryLoader` and `PyPDFLoader`.

- ✂️ **Text Chunking**: 
  Large PDF content is split into smaller, overlapping chunks using `RecursiveCharacterTextSplitter` to improve retrieval precision.

- 🧠 **HuggingFace Embeddings**: 
  Each text chunk is embedded using the `all-MiniLM-L6-v2` model from HuggingFace to generate dense vector representations.

- 📌 **Vector Search with Pinecone**: 
  Embedded chunks are stored in a Pinecone index, enabling fast and accurate semantic retrieval of relevant document sections.

- 🔁 **Retrieval-Augmented Generation (RAG)**: 
  Combines vector search with a GPT-4o language model to generate fact-based, context-aware answers using LangChain's RAG pipeline.

- 🤖 **GPT-4o via OpenRouter**: 
  Uses OpenRouter’s GPT-4o model to generate concise, accurate responses with a custom system prompt limited to three sentences.

- 💬 **Interactive Chat Interface**: 
  A simple Flask-powered web interface allows users to ask natural language questions and receive instant answers from the indexed PDF content.

- 🔐 **Secure Configuration**: 
  API keys for OpenRouter and Pinecone are stored securely using environment variables (`.env` file) loaded with `python-dotenv`.

- 🧪 **Testable & Modular Codebase**: 
  Organized into modular components (`helper.py`, `prompt.py`, `app.py`) for easier debugging, expansion, and maintenance.


---

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

---

## 📄 License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).  
You are free to use, modify, and distribute this software with proper attribution.  

---

## Screenshots

Frontend

![App Screenshot](https://github.com/airakibul/Medical-ChatBot/blob/main/screenshots/screenshot1.png)


![App Screenshot](https://github.com/airakibul/Medical-ChatBot/blob/main/screenshots/screenshot2.png)