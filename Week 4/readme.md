# Week 4 – Comparison of BPE, WordPiece and SentencePiece Tokenizers

## 📌 Project Overview

Week 4 focuses on understanding and comparing different subword tokenization techniques used in Natural Language Processing (NLP) and Large Language Models (LLMs).

Tokenization is the process of converting input text into smaller units called tokens. These tokens may represent complete words, parts of words, punctuation marks, or character-related units. Language models use these tokens by converting them into numerical token IDs.

In this practical, three pretrained tokenizers are implemented using Python and the Hugging Face Transformers library:

1. Byte Pair Encoding (BPE) – GPT-2
2. WordPiece – Multilingual BERT
3. SentencePiece – XLM-RoBERTa

The experiment compares how these tokenizers split the same sentences into smaller token pieces across three languages: English, Telugu, and Hindi.

The main goal is to observe the differences in tokenization methods, token IDs, and total token counts for different languages.

## 🎯 Objectives

- Understand the concept of tokenization and its importance in LLMs.
- Learn the difference between word-level and subword-level tokenization.
- Understand Byte Pair Encoding (BPE), WordPiece, and SentencePiece.
- Implement pretrained tokenizers using Python.
- Compare tokenization results for English, Telugu, and Hindi.
- Observe how different tokenizers split the same input sentence.
- Display token pieces, token IDs, and token counts.
- Understand why token counts differ across tokenizer vocabularies and training data.

## 🛠️ Technologies and Tools Used

- **Programming Language:** Python
- **Library:** Hugging Face Transformers
- **Tokenizer Models:** GPT-2, Multilingual BERT, XLM-RoBERTa
- **Additional Library:** SentencePiece
- **Code Editor:** Visual Studio Code
- **Environment:** Python Virtual Environment
- **Version Control:** Git and GitHub

## 📂 Project Structure

```text
Week4/
│
├── requirements.txt
├── tokenizer_comparison.py
└── README.md
```

### File Description

- **requirements.txt:** Contains the required Python libraries, Transformers and SentencePiece.
- **tokenizer_comparison.py:** Contains the Python program to load pretrained tokenizers, process multilingual text, and compare tokenization results.
- **README.md:** Provides project information, implementation steps, and documentation.

## 📖 Theory

### 1. What is Tokenization?

Tokenization is the process of breaking a sentence or text into smaller units called tokens.

For example:

Input:
"Artificial intelligence is changing the world."

The tokenizer divides this sentence into smaller pieces that can be converted into numerical IDs and processed by a language model.

### 2. Byte Pair Encoding (BPE)

BPE is a subword tokenization technique that repeatedly merges frequently occurring adjacent symbol pairs to create larger token units.

**Model Used:** GPT-2

### 3. WordPiece

WordPiece uses a learned subword vocabulary. If a complete word is not available in the vocabulary, it divides the word into smaller meaningful pieces.

**Model Used:** bert-base-multilingual-cased

### 4. SentencePiece

SentencePiece is a language-independent tokenization framework that learns subword units directly from raw text without requiring pre-tokenized words.

**Model Used:** xlm-roberta-base

XLM-R uses SentencePiece with a BPE model.

## ⚙️ Implementation Steps

### 1. Open the Project in VS Code

Open the Week4 folder in Visual Studio Code and select Terminal → New Terminal.

### 2. Activate the Existing Virtual Environment

Run the following command in PowerShell:

```powershell
..\.MyEnv\Scripts\Activate.ps1
```

### 3. Create requirements.txt

Add the following libraries:

```text
transformers
sentencepiece
```

### 4. Install Required Libraries

Execute:

```bash
pip install -r requirements.txt
```

### 5. Create tokenizer_comparison.py

Import the required library:

```python
from transformers import AutoTokenizer
```

### 6. Define Tokenizers

Configure the three pretrained tokenizer models:

```python
TOKENIZERS = {
    "BPE - GPT-2": "gpt2",
    "WordPiece - Multilingual BERT": "bert-base-multilingual-cased",
    "SentencePiece - XLM-R": "xlm-roberta-base"
}
```

### 7. Define Multilingual Input Text

Use the following sentences for comparison:

```python
TEXTS = {
    "English": "Artificial intelligence is changing the world.",
    "Telugu": "కృత్రిమ మేధస్సు ప్రపంచాన్ని మారుస్తోంది.",
    "Hindi": "कृत्रिम बुद्धिमत्ता दुनिया को बदल रही है।"
}
```

### 8. Load the Tokenizers

Use the `AutoTokenizer.from_pretrained()` function to load the pretrained tokenizer models.

The program loads all three tokenizers and stores them for comparison.

### 9. Compare Tokenizers

The `compare_tokenizers()` function processes each language using all three tokenizers.

For each tokenizer, it performs the following operations:

- Converts the input text into token IDs.
- Extracts the token pieces.
- Displays the token IDs.
- Calculates the total number of tokens.

### 10. Execute the Program

Run the following command:

```bash
python tokenizer_comparison.py
```

The program downloads the pretrained tokenizer files during the first run and displays the comparison results in the terminal.

## 🔄 Working Process

1. Start the Python program.
2. Load the three pretrained tokenizer models.
3. Select the input language.
4. Pass the same input sentence to each tokenizer.
5. Convert the sentence into token IDs.
6. Convert token IDs into readable token pieces.
7. Calculate the total token count.
8. Display the results for each tokenizer.
9. Repeat the process for English, Telugu, and Hindi.
10. Compare the tokenization results.

## 📊 Tokenizer Comparison

| Tokenizer | Model Used | Basic Approach |
|---|---|---|
| BPE | GPT-2 | Merges frequent adjacent symbol pairs |
| WordPiece | Multilingual BERT | Uses learned subword vocabulary |
| SentencePiece | XLM-RoBERTa | Learns subword units directly from raw text |

## 📌 Output Details

The program displays the following information for each language:

**1. Language:** Shows whether the input is English, Telugu, or Hindi.

**2. Input Text:** Displays the original sentence given to the tokenizer.

**3. Tokens:** Shows how the tokenizer divides the sentence into smaller pieces.

**4. Token IDs:** Displays the numerical IDs assigned to the tokens.

**5. Token Count:** Displays the total number of tokens generated by each tokenizer.

The exact tokens, IDs, and counts depend on the pretrained tokenizer files.

## 🧠 Important Observations

- Different tokenizers can divide the same sentence differently.
- English-trained GPT-2 may split Telugu and Hindi text into more tokens than multilingual tokenizers.
- Multilingual tokenizers are designed to handle multiple languages.
- Token counts depend on the tokenizer vocabulary and training data.
- A lower token count does not always mean that a tokenizer is better.
- Token IDs are numerical representations used by language models.

## 📚 Learning Outcomes

Through this experiment, I learned:

- What tokenization means and why it is required in LLMs.
- How words are divided into smaller subword units.
- How BPE, WordPiece, and SentencePiece work.
- How to use Hugging Face Transformers.
- How to load pretrained tokenizer models.
- How to process English, Telugu, and Hindi text.
- How to obtain token pieces and token IDs.
- How to compare token counts across different tokenizers.
- Why multilingual tokenization is important in NLP applications.

## 🚀 Future Improvements

- Compare more pretrained tokenizer models.
- Test additional Indian and international languages.
- Build a simple user interface for entering custom sentences.
- Visualize token counts using graphs.
- Compare tokenization results for longer paragraphs.
- Explore how tokenization affects LLM input length and processing cost.

## 📝 Conclusion

This Week 4 experiment helped me understand the importance of tokenization in Natural Language Processing and Large Language Models. By implementing BPE, WordPiece, and SentencePiece, I learned how different tokenizers divide text into smaller subword units.

The comparison of English, Telugu, and Hindi sentences helped me observe differences in token pieces, token IDs, and token counts. I also understood that tokenization results depend on the vocabulary and training data of each pretrained model.

Overall, this practical provided a basic understanding of multilingual tokenization and how text is converted into numerical representations before being processed by language models.
