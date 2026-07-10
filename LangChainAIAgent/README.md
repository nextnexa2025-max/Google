🚀 LangChain AI Agent with OpenRouter LLM

A modular AI Agent built using LangChain, OpenRouter, FAISS, and HuggingFace embeddings, featuring:

✔️ Web search tool (DuckDuckGo)

✔️ Web scraping tool

✔️ File‑download tool

✔️ RAG (Retrieval Augmented Generation)

✔️ Conversational memory

✔️ Tool‑enabled LLM agent

✔️ Google Colab‑ready setup



This project is designed for experimentation, learning, and building real AI agents with tool‑use capabilities.



📌 Overview

This notebook demonstrates how to build an AI agent capable of:



Running DuckDuckGo web searches



Scraping webpages and saving text



Downloading files from URLs



Performing RAG on uploaded documents



Maintaining chat history



Using OpenRouter LLMs inside LangChain



Triggering tools manually via natural language commands



It’s a complete starter template for building your own AI assistant.



📦 Installation

Install all required dependencies:



bash

pip install langchain langchain-openrouter python-dotenv requests

pip install langchain-community langchain-text-splitters langchain-huggingface sentence-transformers

pip install faiss-cpu

🔑 Environment Setup

Set your OpenRouter API key inside Google Colab:



python

import os

from google.colab import userdata



os.environ\["OPENROUTER\_API\_KEY"] = userdata.get('OPENROUTER\_API\_KEY')

🤖 LLM Initialization

python

from langchain\_openrouter import ChatOpenRouter



llm = ChatOpenRouter(

&#x20;   model="openai/gpt-4o-mini"

)

Test the model:



python

test\_message = "Hello, how are you?"

test\_response = llm.invoke(test\_message)

print(test\_response.content)

🛠️ Tools Included

🔍 Web Search Tool (DuckDuckGo)

python

@tool

def web\_search(query: str):

&#x20;   ...

📥 File Download Tool

python

@tool

def create\_file\_from\_url(url: str):

&#x20;   ...

🕸️ Web Scraping Tool

python

@tool

def scrape\_and\_save(url: str):

&#x20;   ...

All tools are registered:



python

tools = \[web\_search, create\_file\_from\_url, scrape\_and\_save]

📄 Document Upload + RAG Setup

Upload a file in Colab:



python

from google.colab import files

uploaded = files.upload()

filename = list(uploaded.keys())\[0]

Split, embed, and index:



python

splitter = RecursiveCharacterTextSplitter(chunk\_size=500, chunk\_overlap=50)

chunks = splitter.split\_text(text)



emb = HuggingFaceEmbeddings(model\_name="sentence-transformers/all-MiniLM-L6-v2")

db = FAISS.from\_texts(chunks, emb)

RAG search:



python

def rag\_search(query):

&#x20;   docs = db.similarity\_search(query, k=3)

&#x20;   return "\\n\\n".join(\[d.page\_content for d in docs])

🧠 Conversational Agent

The chat() function handles:



Manual tool triggers



RAG queries



Chat history formatting



LLM invocation with tools



Example:



python

response = chain.invoke({

&#x20;   "history": formatted\_history,

&#x20;   "input": message

})

Manual triggers include:



search document <query>



web search <query>



create\_file\_from\_url <url>



scrape <url>



💬 Interactive Chat Loop

python

while True:

&#x20;   user\_input = input("You: ")

&#x20;   if user\_input.lower() == "exit":

&#x20;       break

&#x20;   print("AI:", chat(user\_input))

🧱 Project Structure

Code

📁 Langchain-AI-Agent/

│── 📄 notebook.ipynb

│── 📄 README.md

│── 📁 files/ (auto-created for downloads \& scraped data)

🎯 Features Summary

Feature	Description

🔍 Web Search	DuckDuckGo API integration

🕸️ Web Scraping	BeautifulSoup text extraction

📥 File Downloader	Save any URL content

📚 RAG	FAISS + HuggingFace embeddings

🧠 Memory	Chat history preserved

🛠️ Tools	LangChain tool binding

🤖 LLM	OpenRouter GPT‑4o‑mini





📺 Creator

This notebook is created by NextNexaOfficial  

👉 YouTube: NextNexaOfficial



📝 License

MIT License — free to use, modify, and distribute.



⭐ Contribute

Pull requests are welcome!

If you build new tools, feel free to add them to the agent.

