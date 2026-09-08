# 🔬 Langchain Multi-Agent Research System

A sophisticated multi-agent AI research assistant built with LangChain that automatically searches the web, gathers information, writes comprehensive reports, and provides critical feedback—all powered by LLMs.

## 🎯 Overview

This project implements an intelligent research pipeline that leverages multiple specialized AI agents to conduct comprehensive research on any topic. The system automates the entire research workflow:

1. **Search Agent** - Finds recent and reliable information using web search
2. **Reader Agent** - Scrapes and extracts content from URLs
3. **Writer Agent** - Compiles findings into structured, professional reports
4. **Critic Agent** - Reviews and scores the generated reports

The system includes both a command-line interface (`main.py`) and an interactive Streamlit web application (`app.py`) for a superior user experience.

## ✨ Features

- **🤖 Multi-Agent Architecture**: Specialized agents for searching, reading, writing, and critique
- **🔍 Advanced Web Search**: Integration with Tavily API for reliable search results
- **📄 Intelligent Content Extraction**: Multi-strategy web scraping using trafilatura and BeautifulSoup
- **📝 AI-Powered Report Writing**: GPT-4o-mini generates structured, professional research reports
- **🎯 Quality Assessment**: Automated criticism and scoring of generated reports
- **🎨 Interactive UI**: Beautiful Streamlit interface with custom styling
- **⚡ Production Ready**: Built with LangChain ecosystem best practices

## 📋 Requirements

- Python 3.11+
- OpenAI API key
- Tavily API key

## 🚀 Quick Start

### 1. Create Environment
```bash
# Using conda
conda create -n langagent python=3.11 -y
conda activate langagent
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Configure API Keys
Create a `.env` file in the project root:
```env
OPENAI_API_KEY=your_openai_api_key
TAVILY_API_KEY=your_tavily_api_key
```

### 4. Run the Application

**Interactive Streamlit Web App:**
```bash
streamlit run app.py
```
Opens at `http://localhost:8501`

**Command-line Research:**
```bash
python main.py
```

## 🏗️ Project Architecture

```
Langchain-Multi-Agent-Research-System/
├── app.py                 # Streamlit web interface
├── main.py               # CLI entry point
├── requirements.txt      # Project dependencies
├── .env                  # API keys (create this)
└── src/
    ├── agents/
    │   └── agents.py     # Search, Reader, Writer, and Critic agents
    ├── pipelines/
    │   └── pipeline.py   # Research execution pipeline
    └── tools/
        └── tools.py      # Web search and scraping tools
```

## 🔧 Technical Stack

### Core Framework
- **LangChain** - Agent orchestration and chain composition
- **OpenAI GPT-4o-mini** - Language model for agents and writing
- **Streamlit** - Interactive web interface

### Tools & Libraries
- **Tavily** - Reliable web search API
- **BeautifulSoup4** - HTML parsing
- **Trafilatura** - Article extraction
- **Readability-lxml** - Content readability enhancement
- **Requests** - HTTP client for web scraping
- **Rich** - Beautiful terminal output

## 📖 Usage

### Using the Streamlit App
1. Run `streamlit run app.py`
2. Enter your research topic
3. Click "Start Research"
4. View real-time progress as agents work through each step
5. Read the final report and critic feedback

### Using the CLI
```python
from src.pipelines.pipeline import run_research_pipeline

result = run_research_pipeline("The impact of AI on the job market in 2026")
print(result["report"])
print(result["feedback"])
```

### Pipeline Output
The research pipeline returns a dictionary containing:
- `search_results` - Web search findings
- `scraped_content` - Detailed content from top sources
- `report` - Final research report
- `feedback` - Critic's evaluation and score

## 🔄 Research Pipeline Flow

```
Topic Input
    ↓
[Search Agent] → Finds 5 recent results
    ↓
[Reader Agent] → Scrapes top URL for details
    ↓
[Writer Chain] → Generates structured report
    ↓
[Critic Chain] → Evaluates quality & provides feedback
    ↓
Final Report & Feedback
```

## 🛠️ Customization

### Change LLM Model
Edit `src/agents/agents.py`:
```python
llm = ChatOpenAI(model="gpt-4", temperature=0)  # Change model here
```

### Adjust Search Results
Edit `src/tools/tools.py`:
```python
results = tavily.search(query=query, max_results=10)  # Increase from 5
```

### Modify Report Structure
Edit the prompts in `src/agents/agents.py` writer_prompt and critic_prompt

## 📦 Dependencies

See `requirements.txt` for complete list:
- langchain ≥ 0.2.0
- langchain-core ≥ 0.2.0
- langchain-community ≥ 0.2.0
- langchain-openai ≥ 0.1.0
- streamlit ≥ 1.0.0
- tavily-python ≥ 0.3.0
- beautifulsoup4 ≥ 4.12.0
- trafilatura
- requests ≥ 2.31.0
- python-dotenv ≥ 1.0.0
- rich ≥ 13.7.0

## 🔐 Security Notes

- Never commit `.env` files to version control
- Keep API keys confidential
- Use `.gitignore` to exclude sensitive files
- Rotate API keys regularly

## 🐛 Troubleshooting

**ModuleNotFoundError**: Ensure all dependencies are installed
```bash
pip install -r requirements.txt
```

**API Key Errors**: Verify `.env` file is in project root and keys are valid

**Slow Search Results**: Tavily rate limits apply; consider adjusting `max_results`

**Web Scraping Issues**: Some sites may block scraping; this is expected and handled gracefully


## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

