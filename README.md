# 🔬 Research Paper QA

![Python 3.11+](https://img.shields.io/badge/Python-3.11%2B-3776AB?style=flat-square&logo=python&logoColor=white) ![MIT License](https://img.shields.io/badge/License-MIT-22c55e?style=flat-square) ![Gemma 4](https://img.shields.io/badge/Gemma_4-Google-4285F4?style=flat-square&logo=google&logoColor=white) ![Privacy-First](https://img.shields.io/badge/Privacy--First-100%25_Local-8b5cf6?style=flat-square) ![Ollama](https://img.shields.io/badge/Ollama-Powered-000000?style=flat-square&logo=ollama&logoColor=white)

**Ask questions about research papers and get cited, context-aware answers — all powered by a local LLM with zero cloud dependency.**

---

## Architecture

```
┌──────────────────────────────────────────────────┐
│               Research Paper QA                  │
│                                                  │
│  ┌──────────┐  ┌──────────┐  ┌──────────────┐   │
│  │   CLI    │  │  Web UI  │  │  REST API    │   │
│  │  (Click) │  │(Streamlit)│  │  (FastAPI)   │   │
│  └────┬─────┘  └────┬─────┘  └──────┬───────┘   │
│       └──────────────┼───────────────┘           │
│              ┌───────┴───────┐                   │
│              │  Core Engine  │                   │
│              │ load_paper()  │                   │
│              │ ask_question()│                   │
│              │ cite & follow │                   │
│              └───────┬───────┘                   │
│              ┌───────┴───────┐                   │
│              │  Ollama LLM   │                   │
│              │   (Gemma 4)   │                   │
│              └───────────────┘                   │
│  ┌───────────────────────────────────────────┐   │
│  │  Exports: markdown | json | text notes    │   │
│  └───────────────────────────────────────────┘   │
└──────────────────────────────────────────────────┘
```

---

## ✨ Key Features

- **Multi-Paper Support** — load one or many .txt papers and query across all of them simultaneously
- **Conversational Q&A** — multi-turn dialogue that preserves full context for follow-up questions
- **Automatic Citations** — answers include [Paper: filename, Section: X] references extracted via regex
- **Follow-Up Suggestions** — LLM-generated suggested questions to deepen your research
- **Export Notes** — save conversation history as Markdown, JSON, or plain text
- **Interactive CLI** — Rich-powered terminal with commands for suggest, history, export, and clear
- **Streamlit Web UI** — browser-based interface for uploading papers and asking questions
- **FastAPI REST API** — /ask, /followup, and /citations endpoints for programmatic access
- **Configurable LLM** — adjust model, temperature, max tokens, and number of follow-up suggestions via YAML
- **100 % Local & Private** — your research papers never leave your machine

---

## 🚀 Quick Start

### Prerequisites

| Requirement | Version |
|-------------|---------|
| Python      | 3.11+   |
| Ollama      | latest  |
| Gemma 4 model | pulled via Ollama |

### Installation

```bash
git clone https://github.com/kennedyraju55/research-paper-qa.git
cd research-paper-qa
pip install -r requirements.txt
ollama pull gemma4
```

### Run

```bash
# CLI — single paper
python -m src.research_qa.cli --paper path/to/paper.txt

# CLI — multiple papers
python -m src.research_qa.cli --paper paper1.txt --paper paper2.txt

# Web UI
streamlit run src/research_qa/web_ui.py

# REST API
uvicorn src.research_qa.api:app --host 0.0.0.0 --port 8019

# Docker
docker compose up
```

---

## 🛠️ Tech Stack

| Component        | Technology             |
|------------------|------------------------|
| Language         | Python 3.11+           |
| LLM              | Gemma 4 via Ollama     |
| CLI Framework    | Click + Rich           |
| Web UI           | Streamlit              |
| REST API         | FastAPI + Uvicorn      |
| Export Formats   | Markdown, JSON, Text   |
| Configuration    | YAML (config.yaml)     |
| Containerization | Docker + Docker Compose|
| Testing          | pytest + pytest-cov    |

---

## 📁 Project Structure

```
research-paper-qa/
├── src/research_qa/
│   ├── core.py        # Paper loading, Q&A, citations, follow-ups
│   ├── cli.py         # Click CLI with interactive Q&A loop
│   ├── web_ui.py      # Streamlit web interface
│   ├── api.py         # FastAPI REST endpoints
│   ├── utils.py       # Logging, sys path setup, note export
│   └── config.py      # YAML config loader
├── common/            # Shared LLM client
├── tests/             # pytest test suite
├── config.yaml        # Default configuration
├── requirements.txt   # Python dependencies
├── Dockerfile         # Container build
└── docker-compose.yml # Multi-service orchestration
```

---

## 👤 Author

**Nrk Raju Guthikonda**

- GitHub: [kennedyraju55](https://github.com/kennedyraju55)
- Dev.to: [https://dev.to/kennedyraju55](https://dev.to/kennedyraju55)
- LinkedIn: [https://www.linkedin.com/in/nrk-raju-guthikonda-504066a8/](https://www.linkedin.com/in/nrk-raju-guthikonda-504066a8/)

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
