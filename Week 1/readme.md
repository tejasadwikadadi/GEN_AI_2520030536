# Week 1 – First LLM API Call Using Google Gemini API

## 📌 Project Overview

Week 1 focuses on understanding and implementing the basic connection between a Python application and a Large Language Model (LLM) using the Google Gemini API.

In this experiment, we create a Python program that communicates with the Gemini AI model and generates responses based on the given text prompts. The main purpose is to understand how AI applications interact with LLMs through API requests.

The program uses the Google GenAI SDK to establish a connection with the Gemini model. The API key is securely stored in a `.env` file instead of directly writing it inside the Python code. The `python-dotenv` library is used to load the API key into the application.

## 🎯 Objectives

- Understand the concept of Large Language Models (LLMs).
- Learn how APIs connect Python applications with AI models.
- Understand the importance of API keys for authentication.
- Install and configure the Google GenAI Python SDK.
- Store API keys securely using environment variables.
- Send prompts to the Gemini model.
- Receive and display AI-generated responses.
- Understand basic error handling and troubleshooting.

## 🛠️ Technologies and Tools Used

- **Programming Language:** Python
- **AI Model:** Google Gemini
- **API:** Gemini API
- **Library:** Google GenAI SDK
- **Environment Management:** Python Virtual Environment
- **Environment Variables:** python-dotenv
- **Code Editor:** Visual Studio Code
- **Version Control:** Git and GitHub

## 📂 Project Structure

```text
week1-llm-call/
│
├── .env
├── .gitignore
├── main.py
├── requirements.txt
└── README.md
```

### File Description

- **main.py:** Contains the Python code to connect with the Gemini API, send prompts, and display generated responses.
- **.env:** Stores the Gemini API key securely.
- **.gitignore:** Prevents sensitive and unnecessary files from being uploaded to GitHub.
- **requirements.txt:** Contains the required Python libraries.
- **README.md:** Provides project information, setup instructions, and documentation
