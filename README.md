# Multi-Model AI Assistant: Watsonx Orchestration

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Flask](https://img.shields.io/badge/Flask-2.0%2B-green)
![LangChain](https://img.shields.io/badge/LangChain-0.1%2B-orange)
![IBM Watsonx](https://img.shields.io/badge/IBM-Watsonx.ai-purple)
![License](https://img.shields.io/badge/License-MIT-yellow)

## 📖 Project Overview

A full-stack AI assistant web application that allows users to interact with multiple Large Language Models (LLMs) through a unified interface. Built with Flask and IBM Watsonx, this application demonstrates model orchestration, dynamic prompt templating, and structured JSON output parsing for sentiment analysis and automated response generation.

The application supports three distinct models:

- **Meta Llama** (`meta-llama/llama-4-maverick-17b-128e-instruct-fp8`)
- **IBM Granite** (`ibm/granite-4-h-small`)
- **Mistral AI** (`mistralai/mistral-small-3-1-24b-instruct-2503`)

Whether you are comparing model outputs, testing prompt engineering strategies, or building a production-ready AI assistant, this project provides a clean and extensible foundation.

---

## ✨ Key Features

- **Multi-Model Support:** Seamlessly switch between Llama, Granite, and Mistral models via a unified API.
- **Structured Output:** Utilizes LangChain's `JsonOutputParser` and Pydantic to enforce strict JSON schemas, extracting summaries, sentiment scores, and suggested responses.
- **Dynamic Prompt Engineering:** Implements model-specific prompt templates (e.g., `<|begin_of_text|>` for Llama, `<s>[INST]` for Mistral) to ensure optimal performance across different architectures.
- **Full-Stack Architecture:** Flask backend handling API requests and a lightweight frontend for user interaction.
- **Performance Monitoring:** Tracks response latency (duration) for each model inference, enabling data-driven model selection.
- **Modular Design:** Separate configuration, model logic, and application layers for easy maintenance and extension.

---

## 🏗️ Architecture & Tech Stack

| Layer | Technology |
|-------|------------|
| Backend | Python, Flask |
| AI Orchestration | LangChain, IBM Watsonx.ai |
| Models | Llama-4-Maverick, Granite-4-h-small, Mistral-Small-3.1 |
| Data Validation | Pydantic |
| Frontend | HTML / JavaScript (via Flask templates) |
| Environment | IBM Skills Network Cloud IDE |

### Data Flow
User Input (Browser)
Flask Route (/generate)
Model Selector (app.py)
JSON Parser
JSON Parser
JSON Parser
Llama Chain
- Watsonx API
• Granite Chain —
— Watsonx API -
• Mistral Chain —
• Watsonx AP| -
Structured JSON Response
Frontend Display
---

## 🧠 Technical Deep Dive

This project goes beyond simple API calls. Here are the key engineering decisions that make it robust:

### 1. Model-Specific Prompt Templating

LLMs are sensitive to their training format. Using the wrong prompt structure degrades performance. I implemented specific templates for each model:

| Model | Prompt Format |
|-------|---------------|
| Llama | `<\|begin_of_text\|><\|start_header_id\|>system<\|end_header_id\|>...` |
| Granite | `<\|system\|>{system_prompt}\n<\|user\|>{user_prompt}\n<\|assistant\|>` |
| Mistral | `<s>[INST]{system_prompt}\n{user_prompt}[/INST]` |

This ensures each model receives input in the format it was trained on, significantly improving output coherence and adherence to instructions.

### 2. Structured JSON Outputs

Instead of returning raw text, the application forces the model to return a structured JSON object:


###3. Model Orchestration
The app. py acts as a controller, dynamically routing requests to the appropriate model instance based on user input. The model. py file initializes and manages the lifecycle of all three LLM instances, ensuring efficient reuse of connections.
4. Pydantic Schema Enforcement
By defining an AIResponse schema with Pydantic, we guarantee that the model's output conforms to a predictable structure. If the model returns malformed JSON, the parser raises an error that can be caught and handled gracefully.

###4. Project structure
multi-model-ai-assistant/
│
├── app.py                  # Flask application and API routes
├── model.py                # Model initialization, prompt templates, and inference logic
├── config.py               # Model parameters and credential configuration
├── llm_test.py             # Script to test all models locally
├── capital.py              # Basic connection test script
│
├── templates/
│   └── index.html          # Frontend UI
│
├── static/                 # (Optional) CSS, JS, images
│
├── requirements.txt        # Python dependencies
└── README.md               # Project documentation

###5. Testing the Models
A standalone test script (11m_test. py) is included to verify that all three models are working correctly:
bash
python 11m_test. py
• Copy
This will send a sample prompt to Llama, Granite, and Mistral and print the responses to the console.

###6. Future Improvements
• Environment Variables: Move API keys to . env files for secure production deployment.
• Streaming Responses: Implement token streaming for real-time chat feedback.
• Conversation Memory: Add
ConversationBufferMemory to maintain context across multiple turns.
• Error Handling: Add retry logic with exponential backoff for API rate limits.
• Dockerization: Create a Dockerfile for containerized deployment.
• Unit Tests: Add pytest tests for each model response function.
• Authentication: Add user authentication for multi-user deployments.
• Model Comparison Dashboard: Build a Ul to compare outputs from all three models side-bv-side

###7. Contribution
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a feature branch (git checkout -b feature/amazing-feature).
3. Commit your changes (git commit -m 'Add amazing feature').
4. Push to the branch (git push origin feature/amazing-feature).
5. Open a Pull Request.

###8. Acknowledgments
• IBM Watsonx.ai for model hosting and inference
• LangChain for the orchestration framework
• IBM Skills Network Labs for the development environment
• Meta, IBM, and Mistral Al for the open-source models used in this project

Contact
For questions or feedback, please reach out:
• GitHub: https://github.com/SamuelOlagbenro
• LinkedIn: https://www.linkedin.com/in/samuel-olagbenro
• Email: Seniola961@gmail.com

* If you found this project helpful, please consider giving it a star!
