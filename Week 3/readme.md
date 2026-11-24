# Week 3 – LLM Monitoring with MongoDB

## 📌 Project Overview

Week 3 focuses on extending the Provider-Agnostic LLM Client developed in Week 2 by introducing LLM monitoring and usage tracking using MongoDB.

The main objective of this experiment is to monitor every Large Language Model (LLM) request and store its usage details in a MongoDB database. The application tracks input tokens, output tokens, total tokens, response latency, and estimated API cost for each request.

The project supports both Google Gemini (cloud-based LLM) and Ollama (locally hosted LLM using Llama 3.2). It uses a common LLM client to communicate with both providers and records their usage information in MongoDB Atlas.

Additionally, request timeouts and retry mechanisms are implemented to handle temporary failures and improve application reliability.

## 🎯 Objectives

- Extend the provider-agnostic LLM client developed in Week 2.
- Capture input and output token usage from Gemini and Ollama.
- Calculate the total tokens used for every LLM request.
- Measure response latency in milliseconds.
- Estimate hosted API cost using configurable token rates.
- Store successful and failed request details in MongoDB.
- Implement request timeouts to avoid waiting indefinitely.
- Add retry mechanisms for temporary API and connection failures.
- Perform unit testing using Python's unittest framework.
- Understand the importance of LLM monitoring and observability.

## 🛠️ Technologies and Tools Used

- **Programming Language:** Python
- **Cloud LLM Provider:** Google Gemini API
- **Local LLM Platform:** Ollama
- **Local Model:** Llama 3.2
- **Database:** MongoDB Atlas
- **Libraries:** google-genai, requests, python-dotenv, pymongo
- **Testing:** unittest, pytest
- **Code Editor:** Visual Studio Code
- **Version Control:** Git and GitHub

## 📂 Project Structure

```text
Week3/
│
├── .env
├── main.py
├── llm_client.py
├── usage_logger.py
├── test_client.py
├── requirements.txt
└── README.md
```

### File Description

- **.env:** Stores the Gemini API key, MongoDB connection string, and configurable token pricing.
- **main.py:** Main application that allows users to select Gemini or Ollama and send prompts.
- **llm_client.py:** Contains the common LLM interface, provider implementations, token tracking, latency measurement, cost estimation, timeout handling, and retry logic.
- **usage_logger.py:** Connects to MongoDB Atlas and stores LLM usage records.
- **test_client.py:** Contains unit tests to verify response generation and usage logging using fake providers and loggers.
- **requirements.txt:** Contains all the required Python libraries.
- **README.md:** Provides project documentation and setup instructions.

## ⚙️ Implementation Steps

### 1. Install Required Packages

Install the required Python libraries:

```bash
pip install google-genai requests python-dotenv pymongo
```

### 2. Generate Gemini API Key

Generate a Gemini API key through Google AI Studio and store it securely in the `.env` file.

### 3. Configure MongoDB Atlas

- Create a MongoDB Atlas account.
- Create a free database cluster.
- Create a database user.
- Allow your computer's IP address through Network Access.
- Get the MongoDB connection string.

### 4. Configure the .env File

Add the following environment variables with your own values:

```env
GEMINI_API_KEY=your_gemini_api_key
MONGODB_URI=your_mongodb_connection_string

GEMINI_INPUT_PRICE_PER_MILLION=0
GEMINI_OUTPUT_PRICE_PER_MILLION=0
```

The token pricing values can be configured according to the selected Gemini model's pricing.

### 5. Create usage_logger.py

Create a UsageLogger class to connect the application with MongoDB Atlas.

Its responsibilities include:

- Establishing a MongoDB connection.
- Creating the `llm_monitoring` database.
- Creating the `api_usage` collection.
- Adding timestamps to usage records.
- Inserting successful and failed request details.
- Retrying failed database writes up to three times.

### 6. Update llm_client.py

Extend the existing LLM client to support monitoring features.

The implementation includes:

- LLMResult class to store generated text and token information.
- GeminiProvider to capture Gemini token usage.
- OllamaProvider to capture local model token usage.
- Latency measurement using `time.perf_counter()`.
- Cost estimation based on input and output token rates.
- Usage logging through MongoDB.
- Request timeouts and retry handling.

### 7. Update main.py

The main program allows users to choose between Gemini and Ollama.

The selected provider processes the prompt through the common LLM client. The generated response and monitoring information are displayed in the terminal.

### 8. Create test_client.py

Create unit tests using:

- FakeProvider to simulate an LLM response.
- FakeLogger to store usage records during testing.
- unittest to verify generated responses and token calculations.

This allows testing without making actual API calls or connecting to MongoDB.

## 🧠 System Architecture

The project follows a modular architecture with the following components:

**1. Gemini Provider**

Connects to the Google Gemini API and generates responses while capturing input and output token usage.

**2. Ollama Provider**

Connects to the locally running Ollama service and generates responses using the Llama 3.2 model.

**3. LLM Client**

Acts as the common interface between the application and selected LLM provider. It measures latency, calculates estimated cost, handles retries, and records usage details.

**4. Usage Logger**

Connects to MongoDB Atlas and stores request information in the database.

**5. MongoDB Atlas**

Stores the monitoring records, including provider name, model, token counts, latency, estimated cost, request status, attempts, and timestamp.

## 🔄 Working Process

1. Start the Python application.
2. Select the LLM provider (Gemini or Ollama).
3. Enter a question or prompt.
4. The selected provider processes the request.
5. The application captures input and output token counts.
6. Response latency is calculated in milliseconds.
7. Estimated API cost is calculated for hosted Gemini requests.
8. Successful request details are sent to MongoDB.
9. If a temporary error occurs, the application retries the request.
10. If the request ultimately fails, the failure details are also logged.
11. The generated response and monitoring information are displayed in the terminal.

## 📊 Monitoring Metrics

The application tracks the following metrics:

| Metric | Description |
|---|---|
| Input Tokens | Number of tokens used in the input prompt. |
| Output Tokens | Number of tokens generated by the model. |
| Total Tokens | Sum of input and output tokens. |
| Latency | Time taken for the request in milliseconds. |
| Estimated Cost | Estimated hosted API cost in USD. |
| Provider | Selected LLM provider (Gemini/Ollama). |
| Status | Indicates whether the request succeeded or failed. |
| Attempts | Number of attempts made for the request. |
| Timestamp | Date and time when the request was logged. |

## 🗄️ MongoDB Database Structure

The application creates the following database and collection:

**Database Name:** `llm_monitoring`

**Collection Name:** `api_usage`

Each document stores the monitoring information of an LLM request.

The MongoDB Atlas output shown in the Week 3 lab guide (page 11) demonstrates the `llm_monitoring` database and its `api_usage` collection containing the recorded usage information.

## 🔁 Timeout and Retry Mechanism

To improve reliability, the application uses request timeouts and limited retries.

- Gemini requests use a 60-second HTTP timeout.
- Ollama requests use connection and read timeouts.
- The LLM client makes up to three attempts for selected temporary errors.
- Retry delays use exponential backoff: 1 second and then 2 seconds.
- Failed requests are recorded in MongoDB with failure details.

Database write operations also have a separate retry mechanism of up to three attempts.

## 🧪 Testing

The `test_client.py` file verifies the common LLM client functionality without requiring an actual AI provider or MongoDB connection.

The test checks:

- Whether the client generates the expected response.
- Whether usage details are logged.
- Whether the total token count is calculated correctly.
- Whether the request status is recorded as successful.

Run the unit tests using:

```bash
python -m unittest test_client.py
```

## ▶️ Running the Application

Install the dependencies:

```bash
pip install -r requirements.txt
```

Run the unit tests:

```bash
python -m unittest test_client.py
```

Start the application:

```bash
python main.py
```

Choose the provider:

- Enter `gemini` to use the Google Gemini API.
- Enter `ollama` to use the locally running Llama 3.2 model.

Enter your prompt and observe the generated response and monitoring details.

## 📚 Concepts Covered

- **Token Tracking:** Measures the number of input and output tokens used by LLMs.
- **Latency Monitoring:** Measures the time taken by each LLM request.
- **Cost Estimation:** Calculates the estimated cost of hosted API usage.
- **MongoDB Logging:** Stores request information in a database.
- **Timeout Handling:** Prevents requests from waiting indefinitely.
- **Retry Mechanism:** Handles temporary failures through repeated attempts.
- **LLM Observability:** Helps monitor model usage, performance, cost, and reliability.
- **Unit Testing:** Verifies application functionality using test cases.

## 🚀 Future Improvements

- Create a dashboard to visualize token usage and API costs.
- Add more LLM providers.
- Generate graphical reports using stored MongoDB data.
- Monitor multiple users and their API requests.
- Add advanced error tracking and logging.
- Implement real-time monitoring of LLM performance.

## 📝 Conclusion

This Week 3 experiment helped me understand how to monitor and track the performance of Large Language Models using MongoDB. By extending the provider-agnostic LLM client, I implemented token tracking, response latency measurement, estimated cost calculation, and database logging.

The integration of Gemini, Ollama, and MongoDB helped me understand how to build a more reliable and observable Generative AI application. I also learned how to handle temporary failures using timeouts and retry mechanisms and how to verify the application using unit testing.

Overall, this experiment provided practical knowledge of LLM monitoring, database integration, API reliability, and observability, which are important for developing real-world Generative AI applications.
