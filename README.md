# FastFlicker

Turn an educational YouTube video into study notes and revision flashcards in a few seconds.

## What it does

1. You paste a YouTube link.
2. FastFlicker pulls the video's title, description and channel, and checks whether it looks educational. Music videos, vlogs and broken links are rejected here, before any tokens are spent.
3. For educational videos, it asks a Groq-hosted Llama model for structured notes and flashcards.
4. The video and the generated material are shown side by side.

You can switch between `llama-3.1-8b-instant` (fast, default) and `llama-3.3-70b-versatile` (higher quality) from the sidebar.

## Stack

Python · Streamlit · Groq API · YouTube metadata · Streamlit Cloud

## Run locally

```bash
git clone https://github.com/Rashi18032006/FastFlicker.git
cd FastFlicker
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Create a `.env` file (it is git-ignored):

```env
GROQ_API_KEY=your_key_here
GROQ_API_URL=https://api.groq.com/openai/v1
GROQ_MODEL=llama-3.1-8b-instant
```

Then:

```bash
streamlit run app.py
```

## Deploying on Streamlit Cloud

Create a new app from this repo with `app.py` as the main file, and add `GROQ_API_KEY` under **App settings → Secrets**. The app reads `st.secrets` first and falls back to `.env` locally.

## License

GPL-3.0
