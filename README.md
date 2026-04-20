# BiblioDrift 📚☕
[![Netlify Live App - Click here to view!](https://img.shields.io/badge/Netlify-Live%20App-5314C4?logo=netlify)](https://gitcanvas-dm.streamlit.app/)

> **"Find yourself in the pages."**

BiblioDrift is a cozy, visual-first book discovery platform designed to make finding your next read feel like wandering through a warm, quiet bookstore rather than scrolling through a database.

## Open Source Events Navigation

[![Nexus Spring of Code- Contributor Guide](https://img.shields.io/badge/Nexus%20Spring%20Of%20Code-Contributor%20Guide-1D4ED8?style=for-the-badge)](Open-Source-Event-Guidelines.md)

## 🌟 Core Philosophy
- **"Zero UI Noise"**: No popups, no aggressive metrics. Just calm browsing.
- **Tactile Interaction**: 3D books that you can pull from the shelf and flip over.
- **Vibe-First**: Search for feelings ("rainy mystery"), not just keywords.

## 🚀 Features (MVP & Roadmap)
- **Interactive 3D Books**: Hover to pull, click to flip and **expand**.
- **Virtual Library**: Realistic wooden shelves to save your "Want to Read", "Currently Reading", and "Favorites" list (Persistent via LocalStorage).
- **Glassmorphism UI**: A soothing, modern interface that floats above the content.
- **AI-Powered Recommendations** (Planned): All book recommendations must be generated exclusively by AI.  
     No manual curation, static lists, or hardcoded recommendations are permitted.
- **Dynamic Popups**: Click a book to see an expanded view with AI-generated blurbs.
- **Curated Tables**: Horizontal scrolling lists based on moods like "Monsoon Reads".

## 🛠️ Tech Stack
- **Frontend**: Vanilla JavaScript, CSS3 (3D Transforms), HTML5
- **API**: Google Books API (Real-time data)
- **Storage**: LocalStorage (MVP), PostgreSQL (Planned)
- **Backend (Planned)**: Python Flask
- **AI (Planned)**: LLM integration for "Bookseller Notes"

## 🤖 Project Structure 
```
BIBLIODRIFT/
├── __pycache__/          # Python cache files
├── assets/               # Images, icons, and static UI assets
├── instance/             # App instance / runtime files
├── mood_analysis/        # Mood & emotion analysis logic
├── purchase_links/       # Book purchase / external links logic
├── script/               # Utility or helper scripts
├── venv/                 # Python virtual environment
│
├── .env.example          # Environment variables template
├── .gitignore
│
├── ai_service.py         # AI-powered recommendation / analysis service
├── app.py                # Main backend application entry point
├── models.py             # Database / data models
├── requirements.txt      # Python dependencies
│
├── app.js                # Frontend JavaScript logic
├── chat.js               # Chat interaction logic
├── library-3d.js         # 3D library visualization logic
│
├── index.html            # Landing / discovery page
├── auth.html             # Authentication (Sign In / Sign Up)
├── chat.html             # Chat interface
├── library.html          # User’s virtual library page
│
├── style.css             # Main stylesheet
├── style-original.backup # Backup of original styles
│
├── CONTRIBUTING.md       # Contribution guidelines
├── LICENSE
├── README.md             # Project documentation
├── CONTRIBUTING.md       # Contribution guide and setup notes
├── PROJECT_DETAILS.md    # Contributor-facing project guide
└── page.png              # Preview / UI reference image
```
## 🤖 AI Recommendation Policy

BiblioDrift follows a **strict AI-only recommendation model**.

- All recommendations must be generated dynamically using AI/LLMs.
- Manual curation, editor picks, static mood lists, or hardcoded book mappings are **not allowed**.
- AI outputs should be based on abstract signals such as:
  - Vibes
  - Mood descriptors
  - Emotional tone
  - Reader intent

This ensures discovery stays organic, scalable, and aligned with BiblioDrift’s philosophy of vibe-first exploration.

## 📦 Installation & Setup

### Frontend (Current MVP)
1. Clone the repository:
   ```bash
   git clone https://github.com/devanshi14malhotra/bibliodrift.git
   ```
2. Open `index.html` in your browser.
   - That's it! No build steps required for the vanilla frontend.

### Backend (Future)
Planned implementation using Python Flask.

##  Screenshots

### Home Page
<img width="1912" height="921" alt="Screenshot 2026-02-09 212125" src="https://github.com/user-attachments/assets/296b478b-f275-45c0-957b-50f6ee3a00c8" />

### Virtual Library
<img width="1912" height="922" alt="Screenshot 2026-02-09 212207" src="https://github.com/user-attachments/assets/a1b9a827-d467-4d3c-a113-848252e13f68" />

### Sign In Page
<img width="1917" height="916" alt="Screenshot 2026-02-09 212225" src="https://github.com/user-attachments/assets/9434fa01-9634-46e3-a20b-15ada676a91c" />


## 🧠 AI Service Integration
To keep the frontend and backend synced, use the following mapping:

| Feature | Frontend Call (`app.js`) | API Endpoint (`app.py`) | Logic Provider (`ai_service.py`) |
| :--- | :--- | :--- | :--- |
| **Book Vibe** | `POST /api/v1/generate-note` | `handle_generate_note()` | `generate_book_note()` |

### API Integration
- **Endpoint**: `POST /api/v1/generate-note`
- **Logic**: Processed by `ai_service.py`

## 📡 API Request & Response Examples

### Endpoint: Generate Book Note

**Method:** POST
**URL:** `/api/v1/generate-note`
**Description:** Generates an AI-powered "bookseller note" based on the book's vibe, mood, and metadata.

---

### Request

**Headers**

```json
{
  "Content-Type": "application/json"
}
```

**Body**

```json
{
  "title": "The Night Circus",
  "author": "Erin Morgenstern",
  "mood": "mysterious, magical, slow-burn romance"
}
```

---

### Response

**Success (200 OK)**

```json
{
  "status": "success",
  "note": "A dreamlike duel unfolds in a wandering circus of shadows and light. Perfect for readers who crave atmospheric magic and quiet intensity."
}
```

**Error (400 Bad Request)**

```json
{
  "status": "error",
  "message": "Missing required fields: title or mood"
}
```

---

### API Flow Explanation

1. Frontend sends a POST request from `app.js` to `/api/v1/generate-note`.
2. The Flask backend (`app.py`) receives the request via `handle_generate_note()`.
3. Input data (title, author, mood) is validated.
4. The request is passed to `generate_book_note()` in `ai_service.py`.
5. The AI model generates a contextual "bookseller note".
6. The backend returns the generated note as a JSON response.
7. Frontend displays the note in the book popup UI.


## 🤝 Contributing
We welcome contributions to make BiblioDrift cozier!

1. Fork the repo.
2. Create a feature branch such as `feature/cozy-mode`.
3. Make your changes and test them locally.
4. Push your branch and open a Pull Request.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the fuller workflow and contribution rules.

## 📄 License
MIT License.

---
*Built by Devanshi Malhotra and contributors, with ☕ and code.*


```bash
If you like this project, please consider giving the repository a ⭐ STAR ⭐.
```
