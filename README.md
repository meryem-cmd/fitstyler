# AI-FitStyler

> A multi-agent AI fashion advisor that analyzes your body type and skin tone from a photo, then retrieves personalized outfit recommendations from a product catalog using RAG.

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat-square&logo=python)
![Streamlit](https://img.shields.io/badge/Streamlit-UI-red?style=flat-square&logo=streamlit)
![LangChain](https://img.shields.io/badge/LangChain-RAG-green?style=flat-square)
![MediaPipe](https://img.shields.io/badge/MediaPipe-CV-orange?style=flat-square)

---

## What It Does

Upload a full-body photo, set your gender, occasion, and budget — the system detects your body type and skin tone using computer vision, then searches a product catalog semantically to return outfit suggestions with trend scores and a matching color palette.

---

## How It Works

```
User Photo + Preferences
        ↓
┌─────────────────────────┐
│   Computer Vision Layer  │
│  body_analyzer.py        │  → Detects body type (slim / curvy / athletic)
│  skin_color_analyzer.py  │  → Detects skin tone + suggests color palette
└─────────────────────────┘
        ↓
┌─────────────────────────┐
│     RAG Retrieval Layer  │
│  rag_system.py           │  → FAISS vector store built from catalog.csv
│  outfit_generator.py     │  → Semantic search: "female curvy party under $50"
└─────────────────────────┘
        ↓
┌─────────────────────────┐
│    Critique Layer        │
│  trend_critic.py         │  → Assigns trend score (7–10/10) + comment
└─────────────────────────┘
        ↓
   Streamlit UI (app.py)
```

---

## Features

- **Body Type Detection** — MediaPipe Pose landmarks + hip-to-shoulder ratio classifies body as slim, curvy, or athletic
- **Skin Tone Analysis** — MediaPipe Face Mesh samples cheek pixels in LAB color space; classifies as fair, wheatish, or dark
- **Color Palette Suggestions** — Returns 6 complementary hex colors based on detected skin tone
- **Semantic Outfit Retrieval** — FAISS + HuggingFace Embeddings (`all-MiniLM-L6-v2`) searches catalog by natural language query
- **Budget & Gender Filtering** — Post-retrieval filter ensures results match user's price ceiling and gender
- **Trend Scoring** — Each suggestion gets a 7–10/10 trend score with a style comment
- **Streamlit UI** — Clean interface with sidebar controls, progress bar, and image display

---

## Tech Stack

| Layer | Technology |
|---|---|
| UI | Streamlit |
| Computer Vision | MediaPipe (Pose + Face Mesh), OpenCV |
| Embeddings | HuggingFace `sentence-transformers/all-MiniLM-L6-v2` |
| Vector Store | FAISS (via LangChain) |
| Data | CSV product catalog (48 items) |
| Language | Python 3.8+ |
| Logging | Python `logging` module → `app_log.txt` |

---

## Project Structure

```
AI-FitStyler/
├── app.py                        # Streamlit entry point
├── data/
│   └── catalog.csv               # Product catalog (name, price, image, body type, occasion, gender)
├── core/
│   └── rag_system.py             # Builds and saves FAISS index from catalog
├── agents/
│   ├── body_analyzer.py          # MediaPipe Pose → body type classification
│   ├── skin_color_analyzer.py    # MediaPipe Face Mesh → skin tone + palette
│   ├── outfit_generator.py       # FAISS semantic search → outfit retrieval
│   └── trend_critic.py           # Trend scoring and commentary
├── faiss_index/                  # Generated after running rag_system.py
├── requirements.txt
└── app_log.txt                   # Auto-generated runtime log
```

---

## Getting Started

### Prerequisites

- Python 3.8 or higher
- pip

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/meryem-cmd/fitstyler.git
cd fitstyler

# 2. Install dependencies
pip install -r requirements.txt
```

### Build the RAG Index (required before first run)

```bash
python core/rag_system.py
```

Expected output:
```
RAG built and saved! Ready for queries.
```

This reads `data/catalog.csv` and creates the `faiss_index/` directory.

### Run the App

```bash
streamlit run app.py
```

Opens at `http://localhost:8501`

---

## Usage

1. Set **Gender**, **Occasion**, and **Budget** in the sidebar
2. Upload a clear, full-body photo
3. The system displays your detected **body type**, **skin tone**, and **color palette**
4. Click **Get Outfit Suggestions** to see up to 3 personalized outfits with prices and trend scores

---

## Known Limitations

| Limitation | Detail |
|---|---|
| Small catalog | 48 items — retrieval quality improves significantly with more data |
| No real LLM | Trend scores are randomized (7–10/10); LLM integration (Ollama/OpenAI) is scaffolded in commented code |
| Image URLs | Sourced from Google/external CDNs — some may break over time |
| No persistence | No database; results are not saved between sessions |
| No AR try-on | Planned feature, not implemented |

---

## Team

| Name | Student ID |
|---|---|
| Maryyam Tanveer | BCSF23M007 |
| Minahil Shahid | BCSF23M012 |
| Hassan Ali Pansota | BCSF23M029 |
| Fatima Mirza | BCSF23M031 |

---

## Academic Context

Built as a final project for an AI/Information Systems course. The architecture demonstrates multi-agent design patterns, computer vision pipelines, and retrieval-augmented generation without requiring cloud APIs or paid LLM access.

## Academic Context

Built as a final project for an AI/Information Systems course. The architecture demonstrates multi-agent design patterns, computer vision pipelines, and retrieval-augmented generation without requiring cloud APIs or paid LLM access.

