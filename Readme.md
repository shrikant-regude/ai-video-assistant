# 🎬 AI Video Assistant

An AI-powered meeting intelligence tool that transcribes, summarizes,
and lets you chat with any YouTube video or local recording.

## ✨ Features
- 🔊 Supports YouTube URLs and local video/audio files
- 📝 Transcription via OpenAI Whisper (English) or Sarvam AI (Hinglish)
- 📋 AI-generated summary, action items, key decisions & open questions
- 💬 RAG-based chat — ask anything about the video content
- 🎨 Clean dark-themed Streamlit UI

## 🧠 Tech Stack

| Layer | Technology |
|-------|------------|
| Audio Processing | yt-dlp, pydub, FFmpeg |
| Speech-to-Text | OpenAI Whisper, Sarvam AI |
| LLM | Mistral AI via LangChain LCEL |
| RAG Pipeline | ChromaDB, HuggingFace sentence-transformers |
| UI | Streamlit |

## 🚀 Setup

### 1. Clone the repo
```bash
git clone https://github.com/sriee45/ai-video-assistant.git
cd ai-video-assistant
```

### 2. Create virtual environment
```bash
python -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Add API keys
```bash
cp .env.example .env
```
Fill in your keys in the `.env` file.

### 5. Run
```bash
streamlit run app.py
```

## 📁 Project Structure

ai-video-assistant/

├── app.py                 # Streamlit UI

├── main.py                # CLI entry point

├── core/

│   ├── transcriber.py     # Whisper + Sarvam STT

│   ├── summarizer.py      # Map-Reduce summarization

│   ├── extractor.py       # Action items, decisions, questions

│   ├── rag_engine.py      # RAG Q&A chain

│   └── vector_store.py    # ChromaDB vector store

└── utils/

└── audio_processor.py # Audio download + chunking


## ⚙️ Environment Variables

Copy `.env.example` to `.env` and fill in your keys:

| Variable | Description |
|----------|-------------|
| `MISTRAL_API_KEY` | Get from [mistral.ai](https://mistral.ai) |
| `SARVAM_API_KEY` | Get from [sarvam.ai](https://sarvam.ai) — only needed for Hinglish |
| `WHISPER_MODEL` | Whisper model size: `tiny`, `small`, `medium` (default: `small`) |
| `SARVAM_STT_MODEL` | Sarvam model version (default: `saaras:v2.5`) |

## 📝 Notes

- First run downloads the Whisper model (~460MB for `small`) — takes 1-2 minutes
- Hinglish mode requires a Sarvam AI API key
- Audio files and vector DB are auto-generated locally and not pushed to GitHub

## 👤 Author

Shrikant Regude — [GitHub](https://github.com/sriee45)