# 🤖 AI Content Automation Pipeline (Multi-Agent)

> **End-to-end automated workflow** for autonomous content generation, orchestrating Local LLMs, Text-to-Speech, and binary file management in a self-hosted, containerized environment.

![n8n](https://img.shields.io/badge/n8n-Automation-ff6d5a?logo=n8n)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker)
![Ollama](https://img.shields.io/badge/Ollama-LLM-000000)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-FCC624?logo=linux)

## 📌 Project Overview

This project demonstrates a production-ready automation pipeline designed to eliminate manual bottlenecks in content creation. It bridges the gap between Generative AI and reliable, traceable system execution, applying software engineering and QA principles (inspired by GxP/CSV standards) to AI workflows.

## 🏗️ Architecture & Workflow

The pipeline is orchestrated via **n8n** and runs entirely within a **Docker** environment:

1. **Trigger & Context:** A scheduled trigger or webhook initiates the flow with a specific topic.
2. **LLM Generation (Ollama):** An HTTP request to a self-hosted Ollama instance (e.g., Qwen2.5 or LLaMA) generates a structured script and a visual prompt.
3. **Data Transformation:** A custom JavaScript node parses, cleans, and formats the LLM output, removing artifacts and preparing variables for downstream nodes.
4. **Audio Synthesis (Edge-TTS):** An SSH node executes `edge-tts` on the host machine, converting the cleaned text into natural-sounding speech (e.g., `es-CL-LorenzoNeural`).
5. **Binary File Management:** The generated `.mp3` is securely written to a mapped Docker volume, ensuring strict permission handling and traceability.
6. **Delivery:** The final assets are dispatched automatically via Telegram Bot API.

## 🛠️ Tech Stack

| Category | Technologies |
|----------|--------------|
| **Orchestration** | n8n (Self-hosted), Webhooks, Cron Jobs |
| **AI / LLMs** | Ollama (Local Inference), Prompt Engineering, JavaScript (Node.js) |
| **Infrastructure** | Docker, Docker Compose, Linux/Ubuntu (SSH, Bash), Oracle Cloud |
| **Media Processing** | Edge-TTS, FFmpeg |
| **Development** | JSON, YAML, Git/GitHub |

## ⚡ Key Features & Business Impact

- **📉 90% Reduction in Manual Effort:** Automates the entire lifecycle from ideation to final asset generation.
- **🔒 Self-Hosted & Private:** Utilizes local LLM inference (Ollama), ensuring zero data leakage to third-party AI providers.
- **🛡️ Production-Grade Reliability:** Implements robust error handling, strict Docker volume mapping for binary files, and traceable execution logs (applying CSV/QA best practices to AI).
- **💰 Cost-Effective:** Designed to run on free-tier cloud infrastructure (Oracle Cloud) or low-power devices (Raspberry Pi).

## 🚀 How to Run Locally

1. **Clone the repository:**

   ```bash
   git clone https://github.com/SebaPharma/automatic-content-text-voice-telegrambot-n8n.git
   cd automatic-content-text-voice-telegrambot-n8n
   ```

2. **Ensure Docker and Docker Compose are installed.**

3. **Start the n8n environment:**

   ```bash
   docker compose up -d
   ```

4. **Access n8n:** Open `http://localhost:5678` in your browser.

5. **Import the Workflow:**
   - Go to Workflows → Import from File.
   - Select the `workflow.json` file included in this repository.
   - Configure your local Ollama endpoint and SSH credentials.

## 📂 Project Structure

```text
.
├── docker-compose.yml       # n8n and PostgreSQL container definitions
├── workflow.json            # Exported n8n workflow template
├── README.md                # Project documentation
└── .env.example             # Environment variables template
```

## 👤 Author

**Sebastián Tapia**  
*Validation Manager & AI Automation Engineer*  
🔗 [LinkedIn](https://www.linkedin.com/in/sebasti%C3%A1n-tapia-maturana-50503b144/) | 🌐 [Portfolio](https://sebapharma.github.io/)

---
*Built with rigor, designed for scale.*
