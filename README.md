# 🧠 Research-Agent

A fully automated LLM-powered workflow that summarizes the latest Agentic AI news and delivers concise summaries via email.

## 🚀 Features

- 📥 Scrapes and ingests AI news content
- ✍️ Summarizes articles using a multi-step agent workflow (`summariser` + `reviewer`)
- ✅ Ensures output quality using structured Pydantic validation
- 📧 Sends summaries via the Sendinblue (Brevo) transactional email API
- 🔁 Retry loop for rejected summaries using LangGraph's conditional branching

## 🛠 Tech Stack

- **LangGraph** – Agent workflow orchestration
- **LangChain** – Prompt templates & LLM I/O
- **OpenAI GPT-4o** – LLM for summarization and review
- **Pydantic** – Structured output validation
- **Sendinblue API** – Email delivery
- **BeautifulSoup** – HTML to Markdown conversion

## 🧩 Workflow

```mermaid
graph TD
    A[Input Search Results] --> B[Scrape + Convert to Markdown]
    B --> C[Summariser Agent (LLM)]
    C --> D[Reviewer Agent (LLM)]
    D -->|Approved| E[Send Email]
    D -->|Rejected| C