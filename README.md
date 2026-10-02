# 🕳️ Deepvault Syndicate

An immersive 3D first-person web experience simulating an underground hidden market, where users navigate a dark gallery and negotiate with an AI-powered dealer through chat.

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.110+-009688?logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-18+-61DAFB?logo=react&logoColor=black)
![Three.js](https://img.shields.io/badge/Three.js-R3F-000000?logo=three.js&logoColor=white)
![Groq](https://img.shields.io/badge/LLM-Groq-orange)

---

## 🎮 Features

- **Fully navigable 3D environment** — First-person controls with WASD movement, arrow-key camera, wall collision, and fog-lit atmosphere built entirely in the browser
- **Spatial audio system** — 3D-positioned voices, ambient rain, lightning, and piano that react to player proximity
- **AI salesman (Johan)** — Powered by LLM; routes queries to pre-cached voiced responses or generates dynamic text replies
- **Animated NPCs** — Walking escort with dialogue subtitles, talking gatekeeper, and pianist, all triggered by proximity
- **Unified deployment** — Single FastAPI server serves both the React frontend and the API backend

---

## 🎬 Demo

[![Watch the Deepvault Syndicate Demo](https://img.youtube.com/vi/IfKlVm9ghrk/maxresdefault.jpg)](https://youtu.be/IfKlVm9ghrk)

▶️ [Watch the full demo on YouTube](https://youtu.be/IfKlVm9ghrk)

---

## 📸 Screenshots

<table> <tr> <td width="50%"> <img src="./deepvault-1.png" alt="Deepvault Screenshot 1" width="100%"> </td> <td width="50%"> <img src="./deepvault-2.png" alt="Deepvault Screenshot 2" width="100%"> </td> </tr> <tr> <td width="50%"> <img src="./deepvault-3.png" alt="Deepvault Screenshot 3" width="100%"> </td> <td width="50%"> <img src="./deepvault-4.png" alt="Deepvault Screenshot 4" width="100%"> </td> </tr> <tr> <td width="50%"> <img src="./deepvault-5.png" alt="Deepvault Screenshot 5" width="100%"> </td> <td width="50%"> <img src="./deepvault-6.png" alt="Deepvault Screenshot 6" width="100%"> </td> </tr> <tr> <td width="50%"> <img src="./deepvault-7.png" alt="Deepvault Screenshot 7" width="100%"> </td> <td width="50%"> <img src="./deepvault-8.png" alt="Deepvault Screenshot 8" width="100%"> </td> </tr> </table>

---

## 📁 Project Structure

```
deepvault/
├── brain/                  # Python backend
│   ├── server.py           # FastAPI server (API + frontend serving)
│   ├── phrases.json        # Cached responses & product catalog
│   ├── voice_cache/        # Pre-generated voice audio (.opus)
│   ├── requirements.txt    # Python dependencies
│   ├── .env.example        # Environment variable template
│   └── .env                # Local env vars (gitignored)
├── ui/                     # React frontend
│   ├── src/
│   │   ├── App.jsx         # Root component, startup preloading
│   │   ├── ThreeScene.jsx  # 3D scene (R3F), NPCs, audio, controls
│   │   ├── Room.jsx        # Chat UI, product list, Johan overlay
│   │   ├── ProductList.jsx # Product cards with buy modal
│   │   └── shared3DAudio.js # Web Audio API singleton
│   ├── public/             # Static assets (models, paintings, audio)
│   ├── index.html
│   ├── vite.config.js
│   └── package.json
├── render.yaml             # Render deployment blueprint
├── build.sh                # Build script
├── .gitignore
└── README.md
```

---

## 🛠️ Tech Stack

| Layer      | Technology                                           |
|------------|------------------------------------------------------|
| Frontend   | React 18, Three.js (React Three Fiber), Web Audio API |
| Backend    | Python 3.10+, FastAPI, Uvicorn                       |
| LLM        | Groq (LangChain), configurable model                 |
| Build      | Vite                                                 |
| Deploy     | Render (or any platform supporting Python + Node)    |

---

## 🚀 Getting Started

### Prerequisites

- **Python** 3.10+
- **Node.js** 18+
- **Groq API Key**

### 1. Setup the backend

```bash
cd brain
pip install -r requirements.txt
cp .env.example .env
# Edit .env and add your GROQ_API_KEY
```

### 2. Build the frontend

```bash
cd ../ui
npm install
npm run build
```

### 3. Run the server

```bash
cd ../brain
python server.py
```

Open **http://localhost:8000** in your browser.

---

## ⚙️ Environment Variables

Set these in `brain/.env` (local) :

| Variable       | Description                      | Default                |
|----------------|----------------------------------|------------------------|
| `GROQ_API_KEY` | Your Groq API key                | *(required)*           |
| `GROQ_MODEL`   | Groq model to use                | `openai/gpt-oss-120b` |
| `LLM_TIMEOUT`  | LLM request timeout (seconds)   | `30`                   |
| `PORT`         | Server port                      | `8000`                 |


---

## 🎛️ Controls

| Action | Input                    |
|--------|--------------------------|
| Walk   | `W` `A` `S` `D`         |
| Look   | `↑` `↓` `←` `→` or Mouse Drag |
| Sprint | `Shift` + `W` `A` `S` `D` |

---
