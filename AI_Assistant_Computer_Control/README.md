# 🤖 AI Assistant With Computer Control (LLM + Tools)

Build a simple AI agent from scratch using Python, Google Colab, and an LLM.

In this project, we create an AI assistant that can do more than just answer questions. By connecting the AI model with tools, the assistant can understand user requests, decide when it needs help from the computer, execute actions, and use the results to respond.

This project demonstrates the basic foundation behind modern AI agents.

---

## 🎯 What You Will Build

A simple AI assistant that can:

✅ Communicate with an AI model  
✅ Understand user instructions  
✅ Use tools when required  
✅ Execute computer commands  
✅ Receive results from tools  
✅ Continue the conversation based on the results  

Example:

**User:**


Create a Python file called hello.py


AI decides it needs a tool:


TOOL:bash

echo 'print("Hello from AI")' > hello.py


The computer executes the command.

The AI receives the result and responds:


Your file has been created successfully.


---

# 🧠 How It Works

The architecture is simple:

             User
              |
              ↓
          AI Model
              |
      Need a tool?
              |
    ----------------
    |              |
   No             Yes
    |              |
 Answer        Execute Tool
                   |
                   ↓
             Tool Result
                   |
                   ↓
             AI Response

The AI does not directly control the computer.

Instead:

**AI decides → Tool executes → Result returns → AI responds**

This is the core idea behind AI agents.

---

# 🏗️ Project Components

## 1. LLM Class

The LLM class connects our application with the AI model.

Responsibilities:

- Create AI connection
- Send conversation history
- Receive responses
- Apply system instructions

---

## 2. Tools Class

The Tools class gives the AI additional abilities.

Currently included:

### Bash Tool

Allows the AI assistant to execute commands.

Examples:


ls


List files.


mkdir project


Create folders.


python script.py


Run Python programs.

---

## 3. Harness Class

The Harness controls the entire interaction.

It manages:

- User input
- AI communication
- Tool execution
- Conversation history

The Harness creates the continuous agent loop:


User Request
↓
AI Decision
↓
Tool Execution
↓
Tool Output
↓
AI Final Response


---

# 🚀 Getting Started

## Requirements

- Python 3.10+
- Google Colab account
- OpenRouter API Key

---

# 🔑 Setup API Key

This project uses Google Colab Secrets.

Add your API key:


OPENROUTER_API_KEY


The notebook securely loads the key without storing it inside the code.

---

# 📦 Installation

Install required package:

```bash
pip install openai
▶️ Run the Notebook

Open:

01_AI_Agent_With_Tools.ipynb

Run each cell in order.

At the end, you can interact with your AI assistant:

Example:

You> show me all files

You> create a folder called AI_Project

You> create a python file

You> run this script
🧪 Example Tasks

Try asking:

File Management
Create a folder named Demo
List all files
Python Execution
Create a Python script that prints hello
Run the Python script
System Information
Show current directory
Show Python version
🧩 Technologies Used
Python
Google Colab
OpenRouter
LLM APIs
OpenAI Python SDK
Bash Commands
🌱 Learning Goals

After completing this project, you will understand:

✅ How AI assistants communicate with LLMs
✅ How tools extend AI capabilities
✅ How AI agents execute actions
✅ How the agent loop works
✅ The foundation behind advanced AI systems

🔮 Future Improvements

Possible extensions:

Add multiple tools
Add file read/write tools
Add Python execution tool
Add web search
Add memory
Add RAG knowledge base
Add MCP tool integration
Add voice interaction
Build a complete Jarvis-style assistant
📺 Video Tutorial

This notebook accompanies:

I Gave My AI Assistant Access to My Computer (Create Files, Run Commands & More)

⭐ Support

If you found this useful:

⭐ Star the repository
📢 Share it with other AI enthusiasts
🚀 Continue building AI agents

Built with curiosity and Python ❤️

This notebook is created by NextNexaOfficial

👉 YouTube: NextNexaOfficial

📝 License

MIT License — free to use, modify, and distribute.