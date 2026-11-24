# Week 2 – Provider-Agnostic LLM Client

## 📌 Project Overview

Week 2 focuses on building a **Provider-Agnostic Large Language Model (LLM) Client** using Python. The main objective is to create a single interface that can communicate with different LLM providers, including a hosted cloud API (Google Gemini) and a locally running model (Ollama).

Instead of writing separate application code for each AI provider, this project uses a common interface that allows users to switch between Gemini and Ollama without changing the main application logic.

The Gemini provider generates responses using the Google Gemini API, while the Ollama provider generates responses using a locally installed Llama 3.2 model. This approach makes the application flexible, reusable, and easier to extend with additional LLM providers.

## 🎯 Objectives

- Understand provider-agnostic LLM architecture.
- Connect Python applications with multiple LLM providers.
- Integrate Google Gemini as a cloud-based LLM provider.
- Install and use Ollama for running local LLM models.
- Download and configure the Llama 3.2 model.
- Implement a common interface using Python Abstract Base Classes (ABC).
- Switch between cloud-based and local AI models.
- Perform unit testing using Python's unittest framework.

## 🛠️ Technologies and Tools Used

- **Programming Language:** Python
- **Cloud LLM Provider:** Google Gemini API
- **Local LLM Platform:** Ollama
- **Local Model:** Llama 3.2
- **Libraries:** google-genai, requests, python-dotenv
- **Testing:** unittest, pytest
- **Code Editor:** Visual Studio Code
- **Version Control:** Git and GitHub

## 📂 Project Structure

```text
Week-2/
│
├── .env
├── llm_client.py
├── main.py
├── test_client.py
├── requirements.txt
└── README.md
```

### File Description

- **.env:** Stores the Gemini API key securely.
- **llm_client.py:** Contains the common LLM interface, Gemini provider, Ollama provider, and LLM client.
- **main.py:** Allows users to select an LLM provider, enter a prompt, and display the generated response.
- **test_client.py:** Contains unit tests to verify the working of the LLM client using a fake provider.
- **requirements.txt:** Contains the required Python libraries.
- **README.md:** Provides project documentation and setup instructions.

## ⚙️ Implementation Steps

### 1. Install Ollama

Download and install Ollama on the local system.

### 2. Check Ollama Installation

Open PowerShell and execute:

```bash
ollama --version
```

### 3. Download Llama 3.2 Model

Execute the following command:

```bash
ollama pull llama3.2
```

### 4. Create Project Files

Create a Week 2 folder in Visual Studio Code and add the required files:
- `.env`
- `llm_client.py`
- `main.py`
- `test_client.py`
- `requirements.txt`

### 5. Install Dependencies

```bash
pip install -r requirements.txt
```

### 6. Configure API Key

Add the Gemini API key inside the `.env` file:

```env
GEMINI_API_KEY=your_api_key
```

### 7. Run the Application

```bash
python main.py
```

Select either Gemini or Ollama and enter your question to receive an AI-generated response.

## 🧠 System Architecture

The project uses a common LLM interface to communicate with different providers.

**1. LLMProvider (Common Interface)**

Defines a common `generate()` method that must be implemented by each provider.

**2. GeminiProvider**

Connects to the Google Gemini cloud API and generates responses using the selected Gemini model.

**3. OllamaProvider**

Connects to the locally running Ollama service through an HTTP API request and generates responses using Llama 3.2.

**4. LLMClient**

Acts as a common client that communicates with the selected provider through the same `generate()` method.

## 🔄 Working Process

1. Start the Python application.
2. Select the provider (Gemini or Ollama).
3. If Gemini is selected, the application loads the API key from `.env`.
4. If Ollama is selected, the application connects to the local Ollama service.
5. Enter a question or text prompt.
6. The selected provider processes the prompt.
7. The generated response is returned to the common client.
8. The response is displayed in the terminal.

## 🧪 Unit Testing

The project includes `test_client.py` to test the functionality of the LLM client.

A FakeProvider is created to return a predefined response without calling an actual AI API.

The test checks whether the LLMClient correctly returns the expected response for a given prompt.

This helps verify the common client functionality independently of external AI services.

## 📚 Learning Outcomes

Through this experiment, I learned:

- How to build a provider-independent LLM application.
- How to connect cloud-based and locally hosted AI models.
- How to use Ollama and download the Llama 3.2 model.
- How to implement abstraction using Python ABC.
- How to use API requests to communicate with local models.
- How to switch between different LLM providers.
- How to perform unit testing using unittest.
- How to organize Python projects using separate modules.

## 🚀 Future Improvements

- Integrate additional LLM providers such as OpenAI.
- Add more locally hosted language models.
- Develop a chatbot interface.
- Add better exception handling.
- Support streaming responses.
- Improve testing for different LLM providers.

## 📝 Conclusion

This Week 2 experiment helped me understand how to build a flexible and reusable LLM application using a provider-agnostic architecture. By integrating Google Gemini and Ollama with Llama 3.2, I learned how to work with both cloud-based and locally hosted AI models through a common interface.

The project also introduced abstraction, modular programming, API integration, and unit testing. These concepts provide a strong foundation for developing scalable Generative AI applications.
