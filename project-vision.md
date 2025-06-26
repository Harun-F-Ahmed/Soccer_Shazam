# ⚽ GoalMatchAI – Project Vision

## 🎯 Overview

GoalMatchAI is an AI-powered application that identifies which professional soccer match a goal came from based on a short video clip. By using computer vision models, OCR, and vector similarity search, the app can return match details like teams, date, and optionally, the goal scorer and minute.

---

## 🛠️ MVP Scope

- **Input**: A 5–15 second video clip of a soccer goal (e.g., user uploads a highlight clip)
- **Output**: 
  - Team A vs Team B
  - Date of the match
  - Player who scored, minute of goal

- **Limitations**:
  - Only supports goals from the **2023 English Premier League** season for now
  - Only works on well-lit, broadcast-style clips with visible scoreboard or jerseys
  - Targeting Top 50 goals as the initial dataset

---

## 📦 Key Components

1. **Data Collection**:
   - Download and trim 50–100 labeled goal clips
   - Save metadata: `filename, team1, team2, date, player, minute`

2. **Feature Extraction**:
   - Extract keyframes from each video (OpenCV or FFmpeg)
   - Run OCR on scoreboard to extract team names and clock (Tesseract/EasyOCR)
   - Generate visual embeddings from frames (OpenAI CLIP or ViT)

3. **Vector Indexing**:
   - Store each goal’s feature embedding in FAISS (or Pinecone) for similarity search

4. **Matching Engine**:
   - Given a new clip, extract features and search for most similar goal in database
   - Combine OCR, visual, and (optional) audio features into a confidence score

5. **Backend API**:
   - FastAPI or Flask server
   - Upload endpoint + result response with metadata

6. **Frontend** (Basic):
   - Simple React interface (or HTML+JS)
   - File upload + top match display with confidence %

---

## 🔄 Project Timeline (Suggested)

| Week | Tasks |
|------|-------|
| 1 | Define scope, collect first 50 goal clips, label metadata |
| 2 | Build frame extractor + OCR pipeline |
| 3 | Extract embeddings, set up FAISS, test matching |
| 4 | Build backend API and connect to frontend |
| 5 | Testing and polish – improve accuracy and UX |

---

## 🧰 Technologies

| Task | Tool |
|------|------|
| Video download/trimming | yt-dlp, ffmpeg |
| Frame extraction | OpenCV |
| OCR | Tesseract, EasyOCR |
| Image embeddings | CLIP (via Hugging Face or OpenAI), ViT |
| Vector search | FAISS (local), Pinecone (cloud) |
| Backend | FastAPI |
| Frontend | React or HTML/JS |
| Hosting | AWS EC2 / Render / Vercel |
| Metadata storage | SQLite or PostgreSQL |

---

## ✅ Success Criteria

- User uploads a goal clip → app returns correct match info ≥ 80% of the time
- End-to-end system working with a sample dataset
- Easy to expand with more goals and leagues in the future

---

## 💡 Future Features (Post-MVP)

- Support for multiple leagues/seasons
- Real-time goal detection from live streams
- Jersey/logo detection with YOLOv8
- Commentary-based matching via Whisper
- Mobile app version

