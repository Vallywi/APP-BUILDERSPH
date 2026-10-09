# AppBuilders PH Hackathon 2026 — 12-Hour Buildable Ideas

> Scope rule for a 12-hour build: **one core feature, one model, one clean demo.**
> Avoid real-time video, custom model training, mobile builds, and multi-service backends.
> The winning demo move is simple: **turn off WiFi and it still works.**

---

## What's realistic in 12 hours (and what's not)

**✅ Doable in 12h**
- A desktop or web app with ONE local model doing ONE job (text, audio-to-text, or single-image vision)
- Ollama / LM Studio / llama.cpp for text; Whisper.cpp for speech; a pre-trained ONNX model for images
- Local RAG over a small set of PDFs/text files
- A clean single-screen UI (Streamlit, Gradio, Next.js, or Electron)

**❌ Too risky for 12h**
- Real-time video analysis / live camera vision
- Training or fine-tuning your own model
- Native mobile app builds (Android/iOS signing, device testing)
- Multiplayer, accounts, cloud sync, complex databases

**Golden rule:** Spend hours 0–1 confirming the model runs locally on your actual laptop. If `ollama run` works, the hard risk is gone.

---

## Top 5 ideas ranked for a 12-hour build

Ranked by: buildability + strength on the two biggest scoring criteria (Problem & Usefulness 25% + Local AI 25%).

### #1 — Hatol: Private On-Device Contract/Document Reader  ⭐ easiest + strong
- **One job:** Upload a PDF → local LLM flags risky clauses and explains them in Taglish.
- **Why local wins (your mandatory answer):** Contracts hold sensitive personal/financial data; sending them to a cloud AI is a privacy risk. Nothing leaves the device.
- **12h stack:** Ollama (Llama 3.2 3B) + a PDF text extractor (PyMuPDF) + simple RAG + **Streamlit** UI. All Python, one file.
- **Demo:** Go offline, drag in a sample employment contract, it highlights a predatory clause and explains it.
- **Why #1:** No audio, no vision, no real-time — just PDF text in, answer out. Lowest technical risk, highest privacy story.

### #2 — Guro: Offline AI Tutor for Students Without Internet  ⭐ great story
- **One job:** A Socratic tutor that explains a topic step-by-step in Tagalog/English and generates a practice quiz.
- **Why local wins:** The students who most need AI tutoring have the least/most-expensive connectivity. One download, infinite offline use, zero per-query cost.
- **12h stack:** Ollama + small instruct model with a "guide, don't give answers" system prompt + **Gradio/Streamlit** chat UI. Optional: RAG over a few curriculum PDFs.
- **Demo:** Offline, ask it to teach quadratic equations; it guides instead of dumping the answer, then quizzes you.
- **Why #2:** Pure text/chat — the simplest possible build. Strong "education equity" narrative judges love.

### #3 — SariSense: Offline Voice Bookkeeper for Sari-Sari Stores
- **One job:** Speak a sale in Taglish → it logs inventory + computes daily profit, fully offline.
- **Why local wins:** Vendors have unreliable data, can't afford subscriptions, and want private records. Runs on a modest laptop.
- **12h stack:** Whisper.cpp (voice→text) + small local LLM (parse "tatlong Coke, piso tubo" into structured data) + SQLite + **Streamlit** UI.
- **Demo:** Offline, say three sales in Taglish, watch the ledger and profit update live.
- **Risk note:** Whisper adds setup time — test Tagalog accuracy early (hour 1). Have a text-input fallback ready.

### #4 — Kusina AI: Offline Pantry-to-Recipe (single-image vision)
- **One job:** Upload ONE photo of ingredients → local vision model lists them → local LLM suggests Filipino recipes.
- **Why local wins:** No per-request cloud cost, works in the kitchen with no WiFi, images stay private.
- **12h stack:** A pre-trained ONNX image-classification/detection model (do NOT train your own) + Ollama LLM for recipes + Streamlit upload UI.
- **Demo:** Offline, upload a photo of random ingredients, get 3 cookable recipes.
- **Risk note:** Vision adds risk; keep it to **uploaded single images**, never a live camera feed.

### #5 — Studyo: Offline Audio Transcriber + Summarizer
- **One job:** Drop an audio file → local transcription → local LLM summary + chapters.
- **Why local wins:** Cloud transcription is costly at scale and slow for long files; local is free after setup and keeps unreleased content private.
- **12h stack:** Whisper.cpp + Ollama LLM for summary/chapters + Streamlit file upload.
- **Demo:** Offline, transcribe a short clip and auto-generate chapters in seconds.

---

## Recommended pick

**Go with #1 (Hatol) or #2 (Guro)** if you want the safest 12-hour win — both are pure text, single-model, one-file apps with a strong "why local" story. Pick #3/#4/#5 only if someone on the team has already run Whisper or ONNX before.

---

## 12-Hour Build Timeline (example: Hatol / Guro)

| Time | Block | Goal |
|------|-------|------|
| **0:00–1:00** | Setup & de-risk | Install Ollama, run `ollama run llama3.2`, confirm it works **offline** on your laptop. Lock scope to ONE feature. |
| **1:00–3:00** | Core AI logic | Get the model doing the one job in a plain Python script (PDF→flags, or chat tutor). Tune the system prompt. |
| **3:00–5:00** | Wire the pipeline | Add PDF parsing / RAG (or quiz logic). Make input → model → output work end to end in the terminal. |
| **5:00–6:00** | **Break / buffer** | Eat. Reassess scope. Cut anything not essential to the demo. |
| **6:00–9:00** | Build the UI | Streamlit or Gradio single screen: input area, "Analyze/Ask" button, clean output. Nothing fancy. |
| **9:00–10:30** | Polish & offline proof | Handle errors, add a sample file, verify it runs with **WiFi off**. Open a network monitor to prove no cloud calls. |
| **10:30–11:15** | Demo + video | Record the ~1-min demo video (pull the plug → it still works). Write the README. |
| **11:15–12:00** | Submit | Public GitHub repo, fill the submission (project name, description, team, "why local" answer), post the X/LinkedIn video with #AppBuildersPH. **Deadline is hard: 10:00 AM Oct 10.** |

### Non-negotiables to hit the criteria
- **Local inference is the core** — never fall back to a cloud AI API for the main feature (25%).
- **It must actually run live** — rehearse the demo twice (20%).
- **Pull the plug in the demo** — strongest proof you can show (15% + 15%).
- **README must answer:** *"Why does this product benefit from running AI locally?"* (required).
- **Disclose** every model, framework, and tool used.

---

## Scope-cutting discipline

If you're behind at the 6-hour mark, cut in this order:
1. Drop RAG → just use the model's built-in knowledge.
2. Drop voice/vision → switch to text input.
3. Drop multi-feature → ship the ONE feature that demos cleanly.

A working single-feature app beats an ambitious broken one every time — judges prioritize a **working product over slides**.

---

*Scoped for the AppBuilders PH Hackathon 2026 (Local AI). Build Day is remote and overnight; submission freezes 10:00 AM, Oct 10 — no extensions.*
