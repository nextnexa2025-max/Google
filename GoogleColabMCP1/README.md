📘 Natural Language to SQL Intelligent Agent with SQLite, MCP Server & Visualization
🚀 Project Overview
This project demonstrates how to build an intelligent, natural‑language‑driven database assistant using:

SQLite for local data storage

Python for database operations

FastMCP to expose database tools as an MCP server

Google Colab AI (ai.generate_text) for NL‑to‑SQL translation

Matplotlib for data visualization

The notebook progressively evolves from simple SQL execution to a fully interactive natural‑language interface capable of generating SQL, running queries, summarizing results, and even creating graphs.

“Welcome to NextNexa! In this module, we'll explore the fundamental concepts of database interaction using Python…”

🗄️ 1. Database Setup & Exploration
✔️ SQLite Database Creation
The notebook creates a local SQLite database demo.db and initializes a sales table with fields:

id (INTEGER, primary key)

product (TEXT)

quantity (INTEGER)

price (REAL)

Sample data inserted includes Laptop, Mouse, Keyboard, and Monitor.

✔️ Data Retrieval with Pandas
The notebook uses:

python
df = pd.read_sql_query("SELECT * FROM sales", conn)
to display the full table for verification.

🧠 2. MCP Server for Database Tools
A full Micro‑Agent Communication Protocol (MCP) server is implemented using FastMCP, exposing tools such as:

get_tables() — list all tables

run_query(query) — execute arbitrary SQL

get_sales_summary() — compute total revenue & total items

“This server will host a set of tools (functions) that our AI agent can call to perform database operations.”

The server runs via:

Code
uvicorn rdbms_mcp_server:app --host 0.0.0.0 --port 8000
🧩 3. Natural Language Interface
✔️ Initial Keyword‑Based NL Interface
The first version of ask_database() uses simple keyword matching:

“table” → get_tables()

“total revenue” → get_sales_summary()

“select” → treat input as raw SQL

✔️ AI‑Powered NL‑to‑SQL Translation
A major upgrade introduces:

nl_to_sql(question) — uses ai.generate_text to convert NL → SQL

clean_sql(sql) — removes markdown fences

Error handling for invalid SQL

Example generated SQL:

Code
SELECT price FROM sales WHERE product = 'laptop';
🔍 4. Intelligent Answer Generation
The function answer_with_data(question, result) uses AI to convert raw SQL results into natural‑language answers:

“Use ONLY the following database result to answer the question.”

This ensures grounded, non‑hallucinated responses.

🔄 5. Case‑Insensitive Query Fallback
If a query returns no rows, the system retries using:

Code
LOWER(product)
This solves issues like “mouse” vs “Mouse”.

📊 6. Data Visualization
Two visualization functions are implemented:

✔️ create_graph(result, question)
Creates a simple bar chart for single‑value results.

✔️ create_comparison_graph(result, question)
Creates comparison bar charts for multi‑column results (e.g., product vs price).

The final ask_database() supports:

“graph …” → basic graph

“compare graph …” → comparison graph

🧪 7. End‑to‑End Examples
The notebook demonstrates:

“how many products we have” → SQL count

“what is price of Mouse” → SQL + fallback

“create graph for price of Mouse” → bar chart

“create compare graph for price of all products…” → comparison chart

📦 Technologies Used
Python 3

SQLite

Pandas

Matplotlib

FastMCP

Uvicorn

Google Colab AI (ai.generate_text)

🧭 Project Structure
Code
├── demo.db
├── rdbms_mcp_server.py
├── notebook.ipynb (your Colab notebook)
└── README.md
🎯 What This Project Teaches
How to build a database‑aware AI agent

How to translate natural language into SQL

How to expose database tools via MCP

How to generate natural‑language answers grounded in data

How to integrate visualization into NL queries