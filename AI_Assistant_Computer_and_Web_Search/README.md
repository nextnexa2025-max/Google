# 🤖 Nexa AI Tool-Using Agent (Google Colab)

A simple AI agent built in **Python** that runs inside **Google Colab** using **OpenRouter** and supports **tool calling**.

The agent can decide whether to:

- 💬 Answer normally using an LLM
- 💻 Execute Bash commands
- 🌐 Search the web using Tavily

This project demonstrates the core ideas behind modern AI agents that use tools instead of relying only on the language model.

---

# Features

- OpenRouter LLM integration
- Google Colab compatible
- Bash tool execution
- Web Search using Tavily API
- Automatic tool selection through prompting
- Multi-step reasoning loop
- Conversation memory
- Easy to extend with additional tools

---

# Architecture

```
                User
                  │
                  ▼
           ┌─────────────┐
           │   Harness   │
           └──────┬──────┘
                  │
                  ▼
           ┌─────────────┐
           │ OpenRouter  │
           │     LLM     │
           └──────┬──────┘
                  │
      ┌───────────┴───────────┐
      │                       │
      ▼                       ▼
 Bash Tool              Web Search Tool
      │                       │
      └───────────┬───────────┘
                  ▼
            Tool Output
                  │
                  ▼
             Final Answer
```

---

# Project Structure

```
project/
│
├── main.py
├── README.md
```

---

# Requirements

Install the required packages.

```bash
pip install openai requests
```

For Google Colab, also use:

```python
from google.colab import userdata
```

---

# API Keys

Create the following secrets inside Google Colab.

| Secret Name | Description |
|-------------|-------------|
| OPENROUTER_API_KEY | OpenRouter API Key |
| tavily | Tavily Search API Key |

---

# Model

Default model:

```
meta-llama/llama-3.1-8b-instruct
```

You can change this by modifying:

```python
MODEL = "meta-llama/llama-3.1-8b-instruct"
```

---

# How It Works

The Harness keeps a conversation with the LLM.

When the LLM wants to use a tool, it returns one of these formats.

## Bash

```
TOOL:bash
<command>
```

Example

```
TOOL:bash
ls
```

The Harness executes the command using Python's `subprocess`.

---

## Web Search

```
TOOL:websearch
<query>
```

Example

```
TOOL:websearch
Latest AI news
```

The Harness sends the query to the Tavily Search API and returns the results to the model.

---

# Agent Loop

```
User
   │
   ▼
Send message to LLM
   │
   ▼
Does response start with TOOL: ?
        │
 ┌──────┴──────┐
 │             │
 No            Yes
 │             │
 ▼             ▼
Return      Execute Tool
Answer          │
                ▼
      Send Tool Output
      back to LLM
                │
                ▼
         Final Response
```

---

# Available Tools

## Bash

Used for:

- Creating files
- Editing files
- Running Python scripts
- Listing directories
- Checking installed packages
- Running shell commands
- Viewing file contents

Example prompts:

```
Create hello.py

List files

Run app.py

Show current directory

Check Python version
```

---

## Web Search

Used for:

- Latest news
- Current events
- Documentation
- Weather
- Recent AI releases
- Real-time information

Example prompts:

```
Latest OpenAI news

Current Bitcoin price

Latest Python version

Recent AI research
```

---

# Example Conversation

```
You

Create hello.py

LLM

TOOL:bash
echo 'print("Hello World")' > hello.py

Executing bash...

Tool Output

(no output)

LLM

The file hello.py has been successfully created.
```

---

# Extending the Agent

Adding a new tool is simple.

### Step 1

Create a new function inside `Tools`.

```python
def calculator(self, expression):
    ...
```

### Step 2

Teach the LLM about the new tool inside the system prompt.

### Step 3

Add handling inside:

```python
execute_tool()
```

Done!

---

# Current Limitations

- Runs one tool at a time
- No streaming responses
- No GUI
- No persistent memory
- Bash commands execute locally inside the Colab runtime
- Limited error recovery

---

# Future Improvements

- Function Calling
- MCP (Model Context Protocol)
- RAG integration
- File system abstraction
- Browser automation
- Vision support
- Code execution sandbox
- Long-term memory
- Voice assistant
- Multi-agent architecture

---

# Technologies Used

- Python
- OpenRouter
- OpenAI Python SDK
- Google Colab
- Tavily Search API
- subprocess
- requests

---

# Educational Purpose

This repository is designed to help developers understand:

- AI agents
- Tool calling
- Prompt engineering
- LLM orchestration
- Multi-step reasoning
- Agent loops
- OpenRouter integration

It provides a minimal but complete implementation that can be extended into more advanced agent frameworks.

---

# License

MIT License

Feel free to use, modify, and improve this project.