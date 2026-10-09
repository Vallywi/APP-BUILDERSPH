# AppBuilders PH Hackathon 2026 — Local AI

> **The Challenge:** *"Build an AI product that remains genuinely useful when the cloud disappears."*
> Create a working product that uses AI running **locally** on a user's device to solve a real problem.
> Show why running AI locally creates an experience that would be difficult, expensive, slow, private, or impossible with a cloud-only approach.

---

## Quick Reference (from the briefing)

### What they're asking for
A working product that uses **local AI inference** to solve a real problem. Any kind of product qualifies:
Productivity · Developer tools · Accessibility · Education · Finance · Gaming · Disaster · Creative tools · Enterprise tools · Computer vision · Personal assistants · Privacy tools

### Rules
**Required**
- Substantially built during the hackathon
- A meaningful part of AI inference executes locally
- A working product, demonstrated live
- Models, APIs, frameworks, and major tools disclosed
- Core Local AI functionality works **without depending entirely on a cloud AI API**

**Allowed**
- Existing open-source models and libraries
- AI-assisted development (Devin, etc.)
- Cloud APIs **as secondary components only**

### Tools you can use
Ollama · LM Studio · llama.cpp · MLX · ONNX · PyTorch · TensorFlow · WebGPU · Core ML · AMD ROCm · DirectML · Hugging Face
Plus open-source LLMs, vision models, and speech models. No specific model, framework, OS, or hardware required.

### Judging criteria (how you'll be scored)
| Weight | Criterion | Question |
|--------|-----------|----------|
| **25%** | Problem & Usefulness | Does it solve a genuine problem for a clear target user? |
| **25%** | Local AI Implementation | Is local inference fundamental, and does it give a meaningful advantage? |
| **20%** | Technical Execution | Does it actually work, reliably enough for a live demo? |
| **15%** | Innovation | Is it meaningfully different? Does Local AI enable something new? |
| **15%** | Product & Demo Quality | Is the UX usable, and is the live demo convincing? |

> **Half the score is usefulness and how real your Local AI is.** Every submission must answer: *"Why does this product benefit from running AI locally?"*

### Key logistics
- **Submission deadline:** 10:00 AM, October 10 — **no extensions**. Code freezes; judges review the repo as of the deadline.
- **Demo Day:** October 10, Cyberzone, SM Makati. Finalists announced 1:00 PM.
- **Pitch format:** 5 min pitch + demo, 3 min judge Q&A = 8 min per team.
- **Submit on:** Cerebral Valley event page (`cerebralvalley.ai/e/appbuildersph-hackathon-2026`). One submission per team, public GitHub repo required.
- **Required post:** X/LinkedIn demo video (~1 min), tag Devin/Cognition, include `#AppBuildersPH`.
- **Prizes:** Grand Champion ₱50,000; WhiteCloak ₱15,000; Cognition/Devin ₱10,000; AMD ₱10,000; People's Choice ₱10,000; Tutorials Dojo ₱10,000 (4 winners).

---

## How these ideas are designed

Every idea below is built so that **local inference is the reason it works** — not a nice-to-have. Each targets the two heaviest criteria (Problem & Usefulness + Local AI Implementation = 50%) by picking problems where cloud is genuinely *worse*: offline settings, privacy-sensitive data, real-time latency, or cost at scale.

Each idea includes:
- **Target user** — the "clear target user" judges want.
- **Why local wins** — your mandatory answer to *"Why does this benefit from running AI locally?"*
- **Local AI stack** — concrete, demo-able tools from the allowed list.
- **Demo moment** — the single thing to show in 5 minutes (ideally: *pull the internet cable and it still works*).

---

## Tier 1 — Strongest alignment (disaster, privacy, offline, cost)

### 1. Lifeline — Offline Disaster-Response Assistant for Barangays
- **Target user:** Barangay officials and rescue volunteers during typhoons/earthquakes when internet and power are down.
- **Why local wins:** During disasters, connectivity is the *first* thing to fail. A cloud assistant is useless exactly when it's needed most. Runs fully offline on a laptop or Android device.
- **What it does:** A local LLM answers first-aid questions, triages reported injuries by severity, drafts SITREP reports, and translates between English/Tagalog/Bisaya for responders — all with zero signal.
- **Local AI stack:** Ollama + Llama 3.2 3B (quantized) for Q&A/triage; Whisper.cpp for voice input in noisy field conditions; a pre-loaded offline first-aid/disaster knowledge pack via RAG.
- **Demo moment:** Turn on airplane mode, speak a casualty report, watch it triage and produce a radio-ready SITREP.
- **Hits:** Problem & Usefulness (disaster = listed theme), Local AI (offline is non-negotiable), Innovation.

### 2. Hatol — Private On-Device Legal & Contract Reader (PH context)
- **Target user:** Freelancers, small business owners, and OFWs reviewing contracts/employment agreements they can't afford a lawyer for.
- **Why local wins:** Contracts contain sensitive personal and financial data. Uploading them to a cloud AI is a privacy and confidentiality risk. Everything stays on the device.
- **What it does:** Reads a contract PDF, flags risky clauses (auto-renewal, penalties, one-sided terms), explains them in plain Tagalog/English, and answers "what happens if I..." questions.
- **Local AI stack:** llama.cpp or LM Studio running a mid-size instruct model; local PDF parsing + RAG; optional cloud *only* for an initial glossary download (secondary component).
- **Demo moment:** Drag in a real-looking employment contract offline; it highlights a predatory clause and explains it conversationally.
- **Hits:** Privacy tools (listed theme), Local AI, Usefulness.

### 3. Kusina AI — Offline Pantry-to-Recipe Vision Assistant
- **Target user:** Households in areas with unreliable/expensive mobile data who want to cook with what they already have.
- **Why local wins:** No per-request cloud cost, works in the kitchen with no WiFi, and image recognition stays private. At scale, cloud vision calls would be expensive and slow.
- **What it does:** Point the camera at your fridge/pantry; a local vision model identifies ingredients, then a local LLM suggests Filipino recipes you can make right now, scaled to servings.
- **Local AI stack:** ONNX Runtime or Core ML with a quantized vision model (e.g., YOLO/MobileNet) for ingredient detection; Ollama LLM for recipe generation.
- **Demo moment:** Scan a messy table of random ingredients live, get three cookable recipes instantly, offline.
- **Hits:** Computer vision + Productivity, Local AI (cost/latency), Demo Quality.

### 4. SariSense — Offline AI Bookkeeper for Sari-Sari Stores
- **Target user:** Micro-retailers (sari-sari stores, palengke vendors) with intermittent connectivity and no accounting skills.
- **Why local wins:** Vendors can't rely on data; financial records are private; and a cloud subscription is unaffordable. Runs on a cheap Android phone.
- **What it does:** Voice/photo-based logging ("tatlong Coke, piso ang tubo") → local speech + LLM parse it into inventory and daily profit. Weekly plain-language insights ("you lose money on load, earn most on snacks").
- **Local AI stack:** Whisper.cpp (Tagalog voice) + small local LLM for parsing/insights; on-device SQLite ledger.
- **Demo moment:** Speak three sales in Taglish, watch the ledger and profit update with no connection.
- **Hits:** Finance (listed theme), Local AI, Usefulness.

---

## Tier 2 — Accessibility, education, and health (strong local-AI justification)

### 5. Tinig — On-Device Real-Time Captioning for the Deaf/HoH (Filipino)
- **Target user:** Deaf and hard-of-hearing Filipinos in classrooms, clinics, and meetings.
- **Why local wins:** Captions must be real-time (cloud round-trips add lag), work anywhere without WiFi, and keep private conversations (medical, personal) off third-party servers.
- **What it does:** Live speech-to-text captioning tuned for Taglish code-switching, running fully on-device with sub-second latency.
- **Local AI stack:** Whisper.cpp or a streaming ONNX speech model with WebGPU acceleration; optional on-device summarization of the conversation.
- **Demo moment:** Have a judge speak Taglish; captions appear live with the laptop offline.
- **Hits:** Accessibility (listed theme), Local AI (latency + privacy), Innovation.

### 6. Guro — Offline AI Tutor for Students Without Reliable Internet
- **Target user:** Public-school and provincial students who can't afford constant data or cloud AI subscriptions.
- **Why local wins:** Educational equity — the students who most need AI tutoring have the least connectivity. One-time download, infinite offline use, no per-query cost.
- **What it does:** A Socratic tutor that explains math/science step-by-step in Tagalog/English, generates practice quizzes from the DepEd-style curriculum, and never gives the answer outright.
- **Local AI stack:** Ollama + a small instruct model with a math-reasoning prompt; local RAG over curriculum PDFs; runs on a modest laptop (judges joked about "potato laptops" — lean into efficiency).
- **Demo moment:** Ask it to teach a quadratic equation offline; it guides rather than dumps the answer.
- **Hits:** Education (listed theme), Local AI (equity/cost), Usefulness.

### 7. Hinga — Private On-Device Mental Health Journaling Companion
- **Target user:** People who want to process stress/anxiety privately without sending feelings to a cloud server.
- **Why local wins:** Mental health data is the most sensitive data there is. Local-only guarantees nothing ever leaves the device — a trust claim no cloud app can make.
- **What it does:** Voice or text journaling; a local LLM reflects back patterns, suggests grounding techniques, and tracks mood over time. Clearly *not* a therapist — a reflective companion.
- **Local AI stack:** LM Studio / Ollama LLM; local sentiment/emotion model; fully encrypted on-device storage.
- **Demo moment:** Pull the network cable, journal an entry, get a thoughtful private reflection — prove it never hits the internet (show network monitor).
- **Hits:** Privacy + Personal assistants, Local AI (privacy is the whole point).
- **Note:** Position carefully as wellness support, not medical advice.

---

## Tier 3 — Developer, creative, and enterprise tools

### 8. Lokal — Fully Offline AI Coding Assistant for Air-Gapped Teams
- **Target user:** Developers at banks, government, and defense orgs where code *cannot* leave the network for compliance reasons.
- **Why local wins:** Enterprises in regulated PH industries are banned from sending source code to cloud AI. A local copilot is the only legal option.
- **What it does:** Code completion, explanation, and refactoring in your editor using a local code model — zero code ever transmitted.
- **Local AI stack:** Ollama + a code model (e.g., Qwen/DeepSeek-Coder quantized); VS Code extension; llama.cpp server backend.
- **Demo moment:** Disconnect from the network and show working autocomplete + "explain this function" on a private repo.
- **Hits:** Developer tools (listed theme), Local AI (compliance), Technical Execution.

### 9. Studyo — On-Device Audio/Podcast Transcription + Chapter Generator
- **Target user:** Content creators and students who record long audio and need transcripts, chapters, and summaries without paying per-minute cloud fees.
- **Why local wins:** Cloud transcription is expensive at scale and slow for long files; local batch processing is free after setup and keeps unreleased content private.
- **What it does:** Drop in an audio file → local transcription, auto-chaptering, searchable transcript, and a shownotes summary.
- **Local AI stack:** Whisper.cpp for transcription; local LLM for chaptering/summarizing; WebGPU for in-browser speed.
- **Demo moment:** Transcribe a 10-minute clip offline and generate chapters in seconds.
- **Hits:** Creative/Productivity tools, Local AI (cost), Demo Quality.

### 10. Bantay — On-Device Smart Security Camera (No Cloud Footage)
- **Target user:** Homeowners and small shops who want smart alerts but refuse to stream their home video to a cloud provider.
- **Why local wins:** Continuous cloud video analysis is expensive and a massive privacy breach. Local vision = alerts without footage ever leaving the premises.
- **What it does:** Runs on a laptop/mini-PC with a webcam; local vision model detects people/packages/unusual motion and sends a local notification — footage never uploaded.
- **Local AI stack:** ONNX/DirectML or AMD ROCm (fits the AMD Award!) with a quantized detection model; local event log.
- **Demo moment:** Walk in front of the camera offline; get an instant "person detected" alert with zero cloud calls.
- **Hits:** Computer vision + Privacy, Local AI, and aligns with the **AMD Award** by using ROCm/DirectML.

---

## Choosing & winning tips

1. **Pick a problem where cloud genuinely fails** (offline, private, real-time, or costly at scale). That single-handedly earns the 25% Local AI score and answers the mandatory question.
2. **The strongest demo move is pulling the plug.** Literally go offline mid-demo. It's the most convincing proof for the 20% Technical Execution + 15% Demo Quality.
3. **Keep the model small and the laptop modest.** The chat jokes about "potato laptops" and "ubos na tokens" hint judges value efficiency on real hardware.
4. **Localize for the PH context** (Taglish, local use cases). It sharpens "clear target user" and differentiates for the 15% Innovation score.
5. **Target a special award on purpose:** use AMD ROCm/DirectML for the **AMD Award**, build with Devin for the **Cognition/Devin Award**, and make the demo delightful for **People's Choice**.
6. **Disclose everything** (models, APIs, frameworks, existing code, AI tools) — it's required and failing to do so risks disputes.

---

*Source: AppBuilders PH Hackathon 2026 briefing slides (Challenge, Rules, Tools, Judging criteria, FAQ 1–7, Prizes, Demo Day schedule). Compiled as idea inspiration — all ideas must be substantially built during the hackathon.*
