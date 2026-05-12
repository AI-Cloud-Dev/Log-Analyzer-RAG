# 📄 Log Analyzer RAG (Minimal Retrieval-Augmented Generation Project)

## 🚀 Overview ##

This project demonstrates a **simple, real-world inspired RAG (Retrieval-Augmented Generation) system**.

Instead of using PDFs (common in demos), this project works with **application logs**, simulating how real systems debug failures using logs.

---

## 🧠 What is RAG?

RAG (Retrieval-Augmented Generation) is a pattern where:

1. Relevant data is **retrieved from a source**
2. A language model **uses that data to generate answers**

👉 In this project:

* Retrieval = searching logs
* Generation = explaining failures using LLM

---

## 🧩 Features

* 📂 File-based log storage (team/day-based)
* 🔍 Keyword-based log retrieval
* 🧠 Smart keyword expansion (e.g., "failed" → "error", "exception")
* 📊 Basic ranking of log relevance
* 🤖 LLM-based explanation of failures (optional extension)

---

## 📁 Project Structure

```
project/
│
├── logs/
│   ├── teamA_2026-04-27.log
│   ├── teamB_2026-04-27.log
│
├── service/
│   ├── service.py      # Core logic (retrieval + generation)
│
├── main.py             # Entry point (test execution)
└── README.md
```

---

## ⚙️ How It Works

### Step 1: User Question

Example:

```
What failed in deployment?
```

---

### Step 2: Keyword Extraction

* Converts question into keywords
* Removes stopwords (e.g., "what", "is", "the")

---

### Step 3: Keyword Expansion

Improves matching using a simple map:

```
"failed" → ["error", "exception", "crash"]
"deployment" → ["deploy", "release"]
```

---

### Step 4: Log Retrieval

* Reads `.log` files from `logs/`
* Matches lines containing keywords
* Scores lines based on relevance
* Returns top matches

---

### Step 5: (Optional) LLM Generation

* Sends logs + question to LLM
* Generates human-readable explanation

---

## 🧪 Example Logs

```
INFO: Deployment started
ERROR: Database connection failed
INFO: Retrying...
EXCEPTION: Timeout occurred
```

---

## ▶️ How to Run

### 1. Clone / Setup

```
git clone <repo>
cd project
```

### 2. Add Logs

Place `.log` files inside:

```
logs/
```

---

### 3. Run Script

```python
from service.service import retrieve_logs

question = "what failed in deployment"
logs = retrieve_logs(question)

print(logs)
```

---

## 📌 Sample Output

```
[teamA_2026-04-27.log] ERROR: Database connection failed
[teamA_2026-04-27.log] EXCEPTION: Timeout occurred
```

---

## 🔥 Future Improvements

* 🔗 Integrate LLM (OpenAI / local model)
* 🧠 Replace keyword search with embeddings
* ☁️ Store logs in S3 / database
* ⚡ Add FastAPI endpoint
* 🤖 Convert into agent (multi-step reasoning)

---

## 🆚 RAG vs Simple Search

| Feature        | This Project             |
| -------------- | ------------------------ |
| Retrieval      | Keyword-based            |
| Context Aware  | Yes                      |
| LLM Integrated | Optional                 |
| Real-world use | Log analysis / debugging |

---

## 🎯 Learning Outcome

After completing this project, you will understand:

* How RAG works beyond PDF demos
* How to design retrieval pipelines
* How to prepare data for LLMs
* Foundations for building AI-powered backend systems

---

## ⚠️ Limitations

* Keyword matching is basic
* No semantic understanding (yet)
* File-based storage (not scalable)

---

## 🧑‍💻 Author

Built as part of hands-on learning for:

* AWS + Python Developer
* AI/ML + RAG Systems
* Real-world backend design

---

## 📌 Next Step

👉 Build an **Agent system**:

* Retrieve logs
* Analyze issue
* Take action (store/report/notify)

---

