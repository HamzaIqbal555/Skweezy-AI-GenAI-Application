# Skweezy AI

## Business Use Case
Skweezy AI addresses the need for efficient content digestion in fast-paced professional environments. Professionals, researchers, and teams can quickly extract key insights from long YouTube videos, websites, PDFs, and documents. Generate summaries in text or audio format to boost productivity, support decision-making, and streamline knowledge sharing.

## Overview
Skweezy AI is a Streamlit-based web application leveraging AI for multi-modal summarization. Powered by Groq's high-speed LLMs and LangChain, it processes diverse inputs and delivers downloadable summaries and interactive chat capabilities.

## Key Features
- YouTube summarization from video metadata and description.
- Website content scraping and summarization.
- Multi-PDF processing and summarization.
- Chat mode for Q&A with document context (PDF, TXT, CSV).
- Audio export (MP3 via gTTS).
- Text download (TXT).
- Responsive UI with system theme adaptation.
- Fast inference using Groq LLM (gpt-oss-120b).

## Quick Start

### Prerequisites
- Python 3.11+
- [Groq API Key](https://console.groq.com/keys) (free tier available)
- Optional: [LangChain API Key](https://smith.langchain.com/) for tracing

### Setup
1. Clone/download the repo:
   ```
   git clone <repo-url>
   cd Skweezy_AI
   ```

2. Install dependencies (using uv recommended):
   ```
   uv sync  # or pip install -r requirements.txt
   ```

3. Create `.env` file:
   ```
   GROQ_API_KEY=your_groq_key_here
   LANGCHAIN_API_KEY=your_langchain_key_here  # Optional
   ```

4. Run the app:
   ```
   streamlit run app.py
   ```
   Opens at http://localhost:8501

## Usage

1. **Select Mode** via top buttons:
| Mode       | Input              | Output                       |
|------------|--------------------|------------------------------|
| YouTube   | Paste URL         | Summary + audio/text download|
| Website   | Paste URL         | Summary + audio/text         |
| PDF       | Upload files      | Combined summary + audio/text|
| Chat      | Type query + file | Conversational responses     |

2. **Downloads**: Each summary provides:
  - Play audio inline
  - Download MP3 (`summary.mp3`)
  - Download TXT (`summary.txt`)

**Note**: YouTube uses video description/metadata (full transcripts blocked by YouTube policy).

## Technical Stack
- Frontend: Streamlit
- Backend: LangChain, Groq LLM
- Processing: yt-dlp, WebBaseLoader, PyPDF2, gTTS, pandas
- Project Management: uv, pyproject.toml

## Customization
- Edit `app.py` for UI changes.
- Modify `GenUtils.py` for summarization prompts.
- Update `YTutilities.py` for YouTube logic.

## Configuration
- **GROQ_API_KEY** (required): Sign up at [console.groq.com](https://console.groq.com)
- **LANGCHAIN_API_KEY** (optional): For LangSmith tracing.

## Troubleshooting
- **No summary?** Check API key, internet.
- **YouTube fails?** Use public videos; private/unlisted not supported.
- **Web scrape fails?** Some sites block bots (app uses UA header).
- **Theme issues?** Toggle system light/dark (macOS: System Settings > Appearance).
- **Deps errors?** `uv sync --dev` or `pip install -r requirements.txt --upgrade`.

## Performance
- **Summary Quality**: Map-reduce for long docs (>6k tokens).
- **Speed**: Groq ~100+ tokens/sec.
- **Limits**: Respects LLM context; chunks large inputs.

## Contributing
1. Fork & PR.
2. Add features (e.g., full RAG with Chroma).
3. Test locally.
4. Update README.

## License
MIT License.

