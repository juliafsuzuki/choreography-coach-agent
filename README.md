# Choreography Coach Agent

> An AI agent that helps competitive ballroom dancers turn a showcase video into a personalized practice app.

Built for the **Google for Startups: AI Agents Challenge 2026 — Track 1**.

## What it does

Choreography Coach is an autonomous agent built with the **Google Agent Development Kit (ADK)** and powered by **Gemini 2.5 Flash**. A competitive dancer hands the agent a showcase video and a dance style — the agent then:

1. Analyzes the music's tempo and beat structure
2. Proposes a phrase-by-phrase practice breakdown aligned to the music
3. Returns a personalized drill plan with timestamps and counts

The end-state vision: the agent autonomously cuts per-phrase MP4 clips and deploys a "Showcase Practice" web app the dancer can drill against.

## Architecture

- **Framework:** Google Agent Development Kit (ADK) for Python
- **Model:** Gemini 2.5 Flash (via Google AI Studio)
- **Pattern:** Single LLM agent + custom function tools
- **Runtime:** Local (`adk web`) and Cloud Run

```
choreography_coach (root_agent)
        │
        ├── analyze_audio_tempo   ← detects BPM + time signature
        └── propose_phrase_breakdown ← proposes practice phrases
```

## Project structure

```
my_agent/
├── .env                # API keys (gitignored)
├── __init__.py         # package init
├── agent.py            # root_agent definition + instruction prompt
└── custom_functions.py # tool implementations
```

## Run locally

```bash
pip install google-adk
cd my_agent
# Add your GOOGLE_API_KEY to .env (get one at aistudio.google.com/apikey)
python3 -m google.adk.cli web --allow_origins "regex:https://.*\.cloudshell\.dev"
```

Then open the web preview and chat with the agent.

## About

Built by [Julia Suzuki](https://github.com/juliafsuzuki), founder of **Truly Human AI** — an AI-first product company building personalized training companions for competitive ballroom dancers.
