# Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS
# 🧠 Medical Chatbot – Flask + LangChain + Pinecone + OpenAI

An end-to-end **medical assistant chatbot** built using **LLMs, LangChain, Pinecone, and Flask**.
It can answer health-related questions using vector-based semantic retrieval and GPT-powered reasoning.
*(This project is for educational purposes and does not provide medical advice.)*

---

## 🚀 Quick Start (Local Setup)

### 1️⃣ Clone the repository

```bash
git clone https://github.com/entbappy/Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS.git
cd Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS
```

### 2️⃣ Create a Conda environment

```bash
conda create -n medibot python= 3.9.7 -y
conda activate medibot
```

### 3️⃣ Install the dependencies

```bash
pip install -r requirements.txt
```

### 4️⃣ Add your API keys in a `.env` file

In the root folder, create a `.env` file:

```
PINECONE_API_KEY=your_pinecone_api_key
OPENAI_API_KEY=your_openai_api_key
```

### 5️⃣ Create and store embeddings to Pinecone

```bash
python store_index.py
```

### 6️⃣ Run the Flask app

```bash
python app.py
```

Then open your browser and go to:

```
http://127.0.0.1:8080
```

You’ll see the chatbot interface (from `templates/chat.html`) running locally.

---

## 🧩 Tech Stack

| Category                 | Tools                                     |
| ------------------------ | ----------------------------------------- |
| **Backend**              | Python, Flask                             |
| **LLM Framework**        | LangChain                                 |
| **Embeddings & Storage** | Pinecone Vector DB                        |
| **LLM Provider**         | OpenAI (GPT models)                       |
| **Frontend**             | HTML, CSS, jQuery, Bootstrap              |
| **Deployment**           | AWS EC2 + ECR + GitHub Actions (optional) |

---

## ☁️ AWS Deployment (Optional)

To deploy the chatbot using **Docker + AWS + CI/CD**:

### 1. Create required AWS resources

* **IAM User** with permissions:

  * `AmazonEC2FullAccess`
  * `AmazonEC2ContainerRegistryFullAccess`
* **ECR Repository** for your Docker image
  Example:

  ```
  873925794895.dkr.ecr.us-east-1.amazonaws.com/medicalbot
  ```

### 2. Launch an EC2 instance (Ubuntu)

Install Docker:

```bash
sudo apt update -y && sudo apt upgrade -y
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```

### 3. Configure GitHub self-hosted runner

In your repo → **Settings → Actions → Runners → New self-hosted runner**
Follow the commands displayed for Ubuntu.

### 4. Add GitHub Secrets

| Secret                  | Description       |
| ----------------------- | ----------------- |
| `AWS_ACCESS_KEY_ID`     | IAM access key    |
| `AWS_SECRET_ACCESS_KEY` | IAM secret key    |
| `AWS_DEFAULT_REGION`    | e.g. `us-east-1`  |
| `ECR_REPO`              | ECR image URI     |
| `PINECONE_API_KEY`      | Your Pinecone key |
| `OPENAI_API_KEY`        | Your OpenAI key   |

### 5. Workflow

1. Code pushed → GitHub Actions triggers build
2. Docker image built and pushed to ECR
3. EC2 runner pulls and runs the latest container

---

## 💡 Project Structure

```
Medical-Chatbot/
│
├── static/
│   └── style.css
├── templates/
│   └── chat.html
│
├── app.py                # Flask main app
├── store_index.py        # Pinecone index builder
├── requirements.txt
├── .env.example
└── README.md
```

---

## ⚠️ Disclaimer

> This chatbot is **not a substitute for professional medical advice**.
> Always consult a qualified healthcare provider for any medical condition or emergency.

---
