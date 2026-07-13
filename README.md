# 🤖 GeminiChat — Premium AI Chatbot

A premium, feature-rich AI chatbot web application powered by **Google Gemini 2.5 Flash**, built with **Python (Flask)** on the backend and a **custom dark glassmorphism UI** on the frontend.

Built for the **K-Hub Batch 2026-27 Junior Developer Intern** task.

---

## ✨ Features

| Feature | Details |
|---|---|
| 🎙️ **Voice Input** | Hands-free voice speech-to-text input via the native Web Speech API |
| 🎨 **Dynamic Themes** | Instant UI theme presets (Midnight Violet, Neon Cyan, Cyberpunk Amber, Sakura Rose, Emerald Green) |
| 💬 **Streaming Responses** | Real-time token-by-token output via Server-Sent Events (SSE) |
| 🧠 **Context Retention** | Multi-turn conversational flow (history sent to Gemini on every turn) |
| 📁 **Chat History** | Fully interactive sidebar to create, view, rename, and delete past conversations |
| 🎭 **AI Personas** | 5 built-in personas (General, Code Expert, Teacher, Creative Writer, Analyst) |
| 🔍 **Search** | Full-text query search across all conversations and messages |
| 📝 **Markdown Rendering** | Support for headers, bold/italic formatting, lists, horizontal rules, and inline HTML |
| 📋 **Copy Code Blocks** | Easy, one-click copy button on every syntax-highlighted code block |
| 📱 **Responsive Design** | Desktop sidebar controls and a custom mobile menu layout |
| 💾 **JSON Storage** | History persisted to `data/conversations.json` for easy backups and file-based zero-overhead data handling |

---

## 🏗️ Project Structure

```
Chatbot/
├── app.py               # Flask server & Gemini API integrations
├── storage.py           # Local persistence CRUD layer (JSON file database)
├── requirements.txt     # Python modules list
├── .env                 # Environment credentials configuration (API key)
├── .env.example         # Environment template reference
├── .gitignore           # File listing git exclusions (caches, logs, credentials)
├── data/
│   └── conversations.json  # Auto-created chat storage
└── public/
    ├── index.html       # Web application single-page interface
    ├── style.css        # Premium dark glassmorphism design variables & dynamic themes
    └── app.js           # Frontend client logic & speech recognition
```

---

## 🚀 Setup & Running

### 1. Clone the repository

```bash
git clone https://github.com/your-username/gemini-chatbot.git
cd gemini-chatbot
```

### 2. Create a virtual environment

```bash
python -m venv venv

# Windows (PowerShell/CMD)
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure your Gemini API key

Get a **free** API key at [Google AI Studio](https://aistudio.google.com/app/apikey), copy `.env.example` to `.env`:

```bash
# Windows
copy .env.example .env

# macOS/Linux
cp .env.example .env
```

Open `.env` and set your key:

```env
GEMINI_API_KEY=AIzaSy...your_actual_key_here
```

### 5. Run the server

```bash
python app.py
```

Open your browser at **[http://localhost:3000](http://localhost:3000)**.

---

## 🔑 API Key Notes

- Get your free key at **https://aistudio.google.com/app/apikey**
- Ensure your Google account has active quota enabled for the Generative Language API.
- **Never commit your `.env` file** — it contains private credentials and is ignored by `.gitignore`.

---

## 📡 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/conversations` | List all conversations |
| `POST` | `/api/conversations` | Create a new conversation |
| `GET` | `/api/conversations/:id` | Get conversation + messages |
| `DELETE` | `/api/conversations/:id` | Delete a conversation |
| `PATCH` | `/api/conversations/:id/title` | Rename a conversation |
| `POST` | `/api/conversations/:id/messages` | Send message (SSE stream) |
| `GET` | `/api/search?q=term` | Full-text search |

---

## 🛠️ Technical Decisions

### Why JSON file storage?
For a single-user intern demo, a flat JSON file offers **zero setup overhead** — no database servers or complicated setups needed. The storage is structured, clean, and easily expandable.

### Why Server-Sent Events (SSE)?
SSE is a native browser API over HTTP. It allows GeminiChat to stream the model responses token-by-token in real time without the overhead of heavy WebSockets setups.

### Why Gemini 2.5 Flash?
We upgraded to **Gemini 2.5 Flash** using the official, modern `google-genai` Python SDK. It features fast response speeds, is cheaper to run, and is perfect for interactive messaging.

---

## 📦 Dependencies

- **`flask`** — Backend server and routing framework.
- **`flask-cors`** — Cross-Origin Resource Sharing handler.
- **`google-genai`** — Official modern Google Gemini Python SDK.
- **`python-dotenv`** — Environment configuration variables loader.

---

## 👩‍💻 Author

**Poojitha** — K-Hub Batch 2026-27 Junior Developer Intern
