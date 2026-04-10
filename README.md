# Local Language Complaint Analyzer
**Author:** Abdirahman Mohamud Abdi | Reg No: BSCCS/2023/64091

## Overview
An NLP system that automatically analyzes customer complaints for small businesses.
Supports English, Swahili, and mixed-language input.

## Features
- Classifies complaints into: Product / Service / Delivery / Other
- Detects sentiment: Positive / Negative / Neutral  
- Handles English + Swahili mixed text
- Stores complaints in SQLite database
- Live stats dashboard with category bar charts
- Urgent (Negative) complaint flagging

## Tech Stack
- Python 3 + Flask
- scikit-learn (TF-IDF + Cosine Similarity)
- SQLite (via built-in sqlite3)
- Pure HTML/CSS/JS frontend (no build step)

## Setup

```bash
pip install flask scikit-learn numpy
python app.py
# Open http://localhost:5050
```

## NLP Architecture

1. **Preprocessing** — lowercase, strip punctuation, remove stopwords (EN + Swahili)
2. **Classification** — TF-IDF vectorizer + cosine similarity against category keyword profiles
3. **Sentiment** — Lexicon-based scoring with negation detection ("not good" → Negative)
4. **Storage** — SQLite table: id, user_name, complaint_text, category, sentiment, timestamp

## Testing Examples

| Complaint | Category | Sentiment |
|-----------|----------|-----------|
| "My order arrived very late" | Delivery | Negative |
| "Your staff were very helpful" | Service | Positive |
| "Product is broken and damaged" | Product | Negative |
| "Bidhaa mbaya sana, imevunjika" | Product | Negative |
| "Huduma mbaya, hawakusaidia" | Service | Negative |
