# 📖 Interactive Story Generator

An AI-powered "Choose Your Own Adventure" web app. Enter a theme, and the app generates a unique branching story with multiple paths, choices, and endings — powered by large language models.

🔗 **Live Demo: (https://story-generator-ten-snowy.vercel.app)

---

## ✨ Features

- 🎨 **Theme-based generation** — enter any theme (fantasy, sci-fi, mystery, etc.) and get a unique story
- 🌳 **Branching narratives** — every choice leads to a different path
- 🏆 **Multiple endings** — including winning and losing outcomes
- ⚡ **Async story generation** — background job processing with real-time status updates
- 💾 **Session-based history** — stories are tied to your browser session via cookies

---

## 🛠️ Tech Stack

**Backend**
- FastAPI (Python)
- SQLAlchemy + SQLite
- LangChain + Groq / OpenAI (LLM-powered story generation)
- Pydantic (structured output validation)

**Frontend**
- React (Vite)
- Axios for API calls

**Deployment**
- Backend hosted on [Render](https://render.com)
- Frontend hosted on [Vercel](https://vercel.com)

---

## 🚀 Getting Started (Local Development)

### Prerequisites
- Python 3.10+
- Node.js 18+
- An API key from [Groq](https://console.groq.com) (free tier) or [OpenAI](https://platform.openai.com)

### 1. Clone the repository
```bash
git clone https://github.com/Thoyaj1718/Story-Generator.git
cd Story-Generator
```

### 2. Set up the backend
```bash
cd backend
python -m venv venv
venv\Scripts\activate      # Windows
# source venv/bin/activate  # macOS/Linux

pip install -r requirements.txt
```

Create a `.env` file inside `backend/` with:
```env
DATABASE_URL=sqlite:///./database.db
API_PREFIX=/api
DEBUG=True
ALLOWED_ORIGINS=http://localhost:5173
GROQ_API_KEY=your_groq_api_key_here
```

Run the backend:
```bash
uvicorn main:app --reload
```
The API will be live at `http://127.0.0.1:8000` — visit `/docs` for the interactive Swagger UI.

### 3. Set up the frontend
Open a new terminal:
```bash
cd frontend
npm install
npm run dev
```
The app will be live at `http://localhost:5173`.

---

## 🌐 Deployment

- **Backend (Render):** deployed as a Python web service, with environment variables configured in the Render dashboard.
- **Frontend (Vercel):** deployed as a static Vite build, with `VITE_API_URL` (or the equivalent config in `util.js`) pointing to the live Render backend URL.

Make sure `ALLOWED_ORIGINS` on the backend includes your deployed frontend's URL to avoid CORS errors.

---

## 📂 Project Structure

```
Story-Generator/
├── backend/
│   ├── core/          # Config, prompts, story generation logic
│   ├── db/            # Database connection setup
│   ├── models/        # SQLAlchemy models
│   ├── routers/        # API route handlers
│   ├── schemas/         # Pydantic request/response schemas
│   └── main.py         # FastAPI entry point
├── frontend/
│   ├── src/
│   │   ├── components/   # React components
│   │   └── util.js       # API base URL config
│   └── index.html
└── README.md
```

---

## 📄 License

This project is open source and available under the MIT License.

---

## 🙌 Acknowledgements

Built following the tutorial by [Tech With Tim](https://github.com/techwithtim).
