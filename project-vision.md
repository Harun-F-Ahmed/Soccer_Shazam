## 1. Planning & Design

1. **Define requirements**  
   - What metadata must you return?  
     - Teams  
     - Date  
     - Competition  
     - Scoreline  
   - User flows  
     - Upload → Processing → Result → Confirmation  

2. **Select APIs & services**  
   - Football data API  
     - API-Football  
     - football-data.org  
     - Sportradar / Opta  
   - OCR provider  
     - Tesseract  
     - Google Cloud Vision API  
   - Audio-fingerprinting service (optional)  
     - ACRCloud  
     - Shazam SDK  

3. **Outline data models**  
   - **ClipRecord**  
     - `clip_url` (S3 path)  
     - `ocr_results` (team names, score, minute)  
     - `competition_id`  
     - `embedding_vector`  
     - `matched_fixture_id`  
   - **MatchFixture**  
     - `fixture_id` (API provider ID)  
     - `home_team` / `away_team`  
     - `competition`  
     - `date`  
     - `scoreline`
