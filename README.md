# ReAct AI Agent — Gemini & Python Document Search

An AI-powered **ReAct (Reasoning + Acting) Agent** built using Google's Gemini API and Python. The agent can understand user questions, decide when to use an external tool, search a document collection, observe the retrieved information, and generate context-aware responses.

Developed as part of Assignment 2.

---

## Overview

Traditional language models generate responses based primarily on their learned knowledge. An AI agent can go a step further by interacting with tools to retrieve additional information before answering.

This project demonstrates the ReAct architecture, where an AI model follows an iterative process:

**Reason → Act → Observe → Reason → Final Answer**

The agent uses Gemini as its reasoning engine and a custom Python document-search function as its tool.

## Key Features

- **Gemini-Powered Agent:** Uses Google's Gemini API to interpret questions and decide when additional information is required.
- **Custom Search Tool:** Implements a Python-based search function to retrieve relevant information from a predefined document collection.
- **ReAct Agent Loop:** Executes repeated reasoning, tool-calling, and observation cycles.
- **Context-Aware Responses:** Uses retrieved document information to generate relevant answers.
- **Tool Calling:** Supports structured function calling between Gemini and Python.
- **Error Handling:** Includes retry logic for temporary API availability and rate-limit errors.
- **Multi-Question Testing:** Evaluates the agent using questions that are both answerable and unanswerable from the available documents.

## Architecture

```text
             USER QUESTION
                   |
                   v
            GEMINI MODEL
                   |
                   v
            REASONING STEP
                   |
             Need information?
                   |
             Yes   |   No
              |    |    |
              v    |    v
        SEARCH TOOL | FINAL ANSWER
              |
              v
       DOCUMENT SEARCH
              |
              v
       RETRIEVED RESULTS
              |
              v
          OBSERVATION
              |
              v
         GEMINI MODEL
              |
              v
       REASONING AGAIN
              |
         Final response
```

## Document Collection

The project uses a predefined collection of Computer Science documents stored in Python.

| Document | Description |
|---|---|
| Stacks | Stack operations and LIFO principles |
| Binary Search | Searching algorithms and time complexity |
| Java OOP | Encapsulation, inheritance, polymorphism and abstraction |
| ReAct Agents | Reasoning, tool calling and observation cycles |

Each document contains multiple sentences to provide information for the search tool.

## How It Works

1. The user submits a question.
2. Gemini processes the question and determines whether it needs additional information.
3. If necessary, Gemini requests the `search_documents` function.
4. Python executes the search function against the document collection.
5. Relevant search results are returned as observations.
6. Gemini uses those observations to continue processing the question.
7. The agent generates its final response.

The agent repeats this process until it produces an answer or reaches its maximum execution-step limit.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core implementation |
| Google Gemini API | AI reasoning and generation |
| Google Gen AI SDK | Gemini API integration |
| Google Colab | Development and execution environment |
| Function Calling | Communication between Gemini and Python |
| Python Dictionary | Document storage |
| Time / Retry Logic | Handling temporary API errors |

## Getting Started

### Prerequisites

- A Google account.
- Access to Google Colab.
- A Gemini API key from Google AI Studio.

### 1. Clone the Repository

```bash
git clone https://github.com/SamyakShankar/ReAct-Agent-Assignment-2.git
```

### 2. Open the Notebook

Open the `.ipynb` file in Google Colab.

Alternatively, upload the notebook directly to Google Colab.

### 3. Configure the Gemini API Key

Get an API key from:

https://aistudio.google.com/apikey

In Google Colab:

1. Open the Secrets panel.
2. Create a secret named `GOOGLE_API_KEY`.
3. Paste your API key as its value.
4. Enable notebook access.

**Important:** Never expose your API key in source code or commit it to a public GitHub repository.

### 4. Install Dependencies

Run the package installation cell in the notebook.

```python
%pip install -q -U google-genai
```

### 5. Execute the Notebook

Run the notebook cells in order:

1. Gemini API key setup.
2. Package installation.
3. Document collection initialization.
4. Search tool implementation.
5. Gemini model configuration.
6. ReAct agent loop implementation.
7. Test questions.
8. Final validation.

## Example Interaction

**User Question:**

What are the main operations of a stack?

**Agent Action:**

```text
Step 1: ACT -> search_documents(
    query='stack operations push pop'
)
```

**Observation:**

```text
A stack is a linear data structure that follows
the Last In First Out principle.

The two main operations are push and pop.
Push inserts an element at the top of the stack,
while pop removes the top element.
```

**Final Answer:**

A stack follows the Last In First Out (LIFO) principle. Its main operations are:

- Push: Inserts an element at the top of the stack.
- Pop: Removes the top element.
- Peek: Returns the top element without removing it.

## Project Structure

```text
ReAct-Agent-Assignment-2/
│
├── ReAct_Agent_Assignment_2.ipynb
│
└── README.md
```

## Learning Outcomes

Through this project, the following concepts were explored:

- Understanding AI agents and the ReAct architecture.
- Integrating large language models through APIs.
- Implementing custom Python tools.
- Understanding function calling.
- Managing model responses and tool observations.
- Implementing iterative agent execution loops.
- Handling API errors and temporary service interruptions.
- Evaluating AI responses using document-based questions.

## Limitations

- The search tool operates on the predefined document collection rather than the public internet.
- Search relevance depends on the contents of the available documents and the keyword-matching implementation.
- The agent's responses are limited by the information retrieved from the document collection.
- Gemini API availability and usage are subject to Google's API limits.

## Author

**Samyak Shankar**

**GitHub:** [SamyakShankar](https://github.com/SamyakShankar)

**Project:** Assignment 2 — ReAct AI Agent

**Environment:** Google Colab

**AI Model:** Google Gemini

---

*This project demonstrates the implementation of a tool-using AI agent through the ReAct reasoning and action cycle.*
