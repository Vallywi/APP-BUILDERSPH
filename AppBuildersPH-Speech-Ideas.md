# AppBuilders PH Hackathon 2026 — Offline Speech + Accessibility Ideas + Implementation

> **Focus:** Offline speech recognition (STT) as the core local AI, applied to **Accessibility / Disability** — a listed hackathon theme.
> **Aligned to the slides:** every idea answers *"Why does this benefit from running AI locally?"*,
> targets the 50% that is Problem&Usefulness + Local AI, and is scoped to fill a real **12-hour** build.
> **Excluded themes:** education, flood/disaster, hospital/medical, government.
> **Note on scope:** these are *assistive/accessibility* tools for daily life (communication, independence), **not** medical/clinical/diagnostic tools.

---

## Why offline speech + accessibility is a strong hackathon bet

Accessibility is a listed theme, and offline STT maps almost perfectly to the judging criteria:

| Criterion | Weight | How offline speech-accessibility scores |
|-----------|--------|------------------------|
| Problem & Usefulness | 25% | Serves a clear, under-served user: people with disabilities who struggle with typing, hearing, or speaking |
| Local AI Implementation | 25% | STT is *real, heavy* inference — clearly fundamental, not a gimmick |
| Technical Execution | 20% | Live "speak/hear → it responds offline" is a convincing, provable demo |
| Innovation | 15% | Taglish + offline assistive tech is badly under-served vs English cloud tools |
| Product & Demo Quality | 15% | An assistive voice demo is emotionally resonant and memorable on stage |

**Your mandatory answer, pre-written:** *"Assistive communication must run on-device because the user depends on it everywhere — including places with no internet — it must respond instantly (lag breaks a conversation), and the audio is deeply personal. Cloud STT is slower, costs per minute, fails without signal, and leaks private speech."*

**Why local matters more for disability users specifically:** an assistive tool that only works with good WiFi isn't an accessibility tool — it's a liability. Independence requires it to work *always*, offline, instantly.

---

## The accessibility ideas (each fills a full 12 hours)

These are intentionally bigger than a toy transcriber — they pair STT with a second local step (structuring, prediction, or translation) so the build genuinely takes 12 hours and the result feels like a real assistive product.

### 1. Tinig — Offline live captioning for the Deaf / Hard-of-Hearing (Taglish)
- **Who:** Deaf and hard-of-hearing Filipinos in everyday conversations — at the store, with family, at work.
- **What:** Someone speaks → offline STT shows **large, live captions** in Taglish on screen. A local LLM optionally cleans up and punctuates the text so it's readable, and can summarize a long conversation.
- **Why local:** Captions must appear *instantly* (cloud lag breaks a real conversation), work anywhere without WiFi, and keep personal conversations off third-party servers.
- **The 12h depth:** chunked near-real-time STT + readable-caption cleanup + a big accessible caption UI + conversation summary.
- **Demo:** WiFi off, a judge speaks Taglish, captions appear live and large on screen.

### 2. Boses — Offline voice for people who struggle to speak (AAC)
- **Who:** People with speech impairments or who are non-verbal, who need a voice to communicate.
- **What:** The user types or taps short Taglish phrases → a local LLM expands shorthand into full natural sentences → optional on-device text-to-speech "speaks" for them. Reverse mode: others speak → offline STT captions it back for the user. A two-way communication bridge.
- **Why local:** This is the user's *voice* — it must work everywhere, instantly, and never depend on signal or leak private conversations.
- **The 12h depth:** shorthand-to-sentence LLM + offline STT for the reverse direction + TTS + an accessible big-button UI.
- **Demo:** Offline, tap "gutom… kain… tayo" → it speaks a full sentence; then a judge replies by voice and it captions back.

### 3. Sigaw — Offline Taglish voice control for hands-free computer use
- **Who:** People with limited mobility / motor disabilities who can't easily use a mouse or keyboard.
- **What:** Say a command in Taglish ("buksan mo ang browser", "gawa ka ng note na…") → offline STT → a local LLM maps it to an intent → the app runs a safe local action (open app, type dictated text, set a timer).
- **Why local:** An always-listening assistive tool can't stream your mic to the cloud (privacy + latency), and must work the moment you speak, every time.
- **The 12h depth:** STT + intent-mapping LLM + a small safe action library + dictation mode.
- **Demo:** Offline, speak 3 Taglish commands hands-free, watch the laptop obey.
- **Risk note:** Keep the action set small and safe (no destructive commands).

### 4. Diktado — Offline voice-to-structured-notes for low-vision / dyslexic users
- **Who:** Low-vision users and people with dyslexia who find typing and reading dense text hard.
- **What:** Speak freely in Taglish → offline STT → a local LLM turns the ramble into clean, well-structured, large-print output you choose: a to-do list, a simple summary, or a formatted message — easy to read aloud back.
- **Why local:** Personal notes stay private, works with no signal, instant, and no per-minute cloud fee for a daily-use assistive tool.
- **The 12h depth:** STT + multiple "output format" LLM modes + a high-contrast/large-text accessible UI + read-back.
- **Demo:** Offline, ramble for 20 seconds, pick "to-do list," get a clean large-print checklist it reads back.

### 5. Hudyat ng Tahanan — Offline sound-awareness alerts for the Deaf
- **Who:** Deaf / hard-of-hearing users at home who can't hear important sounds (doorbell, someone calling their name, an alarm, a knock).
- **What:** The laptop/phone listens locally; an on-device audio model recognizes key sounds and spoken "name calls," then flashes a big visual + vibration alert. STT handles the "someone said your name / said tulong" case.
- **Why local:** Continuous audio monitoring to the cloud is a massive privacy breach and useless without signal; alerts must be instant to matter.
- **The 12h depth:** continuous local audio capture + sound/keyword detection (STT for speech triggers) + an alert UI. Keep the trigger set small and well-tuned.
- **Demo:** Offline, say the user's name or knock near the mic → a bold on-screen flash alert fires.
- **Risk note:** This is *awareness assistance for daily life*, not a safety/medical device — frame it that way.

### 6. Senyas — Offline two-way bridge between speech and text for mixed groups
- **Who:** Deaf and hearing people trying to talk in the same room (family dinners, workplace huddles).
- **What:** Split screen. The hearing person speaks → offline STT captions it for the Deaf user; the Deaf user types short Taglish → a local LLM expands it into a natural sentence shown large (and optional TTS) for the hearing person. One shared device, both directions.
- **Why local:** A shared, always-on conversation tool can't depend on signal or ship private family talk to the cloud; turn-taking needs instant response.
- **The 12h depth:** bidirectional pipeline (STT one way, LLM expand + TTS the other) + a clean split-screen UI + turn indicator.
- **Demo:** Offline, a judge speaks → caption appears on one side; type "salamat… tulong… bukas" → full spoken sentence on the other side.

### 7. Alalay — Offline voice reminder & routine assistant for cognitive support
- **Who:** Users with memory, attention, or cognitive disabilities (and elderly users) who need gentle spoken reminders and simple step-by-step guidance.
- **What:** Speak a reminder or routine in Taglish ("alalahanin mo ako uminom ng gamot pagkatapos mag-almusal") → offline STT → a local LLM structures it into timed reminders and breaks tasks into simple steps it can read back one at a time.
- **Why local:** Routines are deeply personal, must fire reliably without internet, and a daily-use assistive tool can't rack up cloud costs. Instant and always-available is the whole point.
- **The 12h depth:** STT + reminder/step-structuring LLM + a simple scheduler + large read-back UI.
- **Demo:** Offline, speak a routine, watch it become simple timed steps it reads back one at a time.
- **Risk note:** Position as daily-living support, not medical/clinical care.

### 8. Basa Pa — Offline read-aloud + simplify for low-vision / dyslexic users
- **Who:** Low-vision and dyslexic users who struggle with dense text, plus anyone who learns better by listening.
- **What:** Paste or load text → a local LLM rewrites it in simpler, clearer Taglish/English → on-device TTS reads it aloud. Reverse mode: speak a question about the text → offline STT → it answers by voice. Speech both in and out.
- **Why local:** Private documents stay on-device, works offline anywhere, and read-aloud of long text on cloud would be slow and costly.
- **The 12h depth:** text-simplify LLM + TTS + STT Q&A loop + high-contrast large-text UI with adjustable speed.
- **Demo:** Offline, load a dense paragraph → it simplifies and reads it aloud; ask a question by voice → it answers.

### 9. Tahimik — Offline "whisper/unclear speech" normalizer for atypical speech
- **Who:** People whose speech is hard for standard tools to understand — slurred, very soft, or affected by a condition — who get misheard by normal voice assistants.
- **What:** The user speaks → offline STT transcribes → a local LLM uses context to reconstruct the most likely intended Taglish sentence and reads it back to confirm, so unclear speech still becomes clear, usable text.
- **Why local:** Highly personal speech patterns are sensitive, the tool must work everywhere, and iterative confirmation needs instant local turnaround.
- **The 12h depth:** STT + a context-aware "best-guess reconstruction" LLM step + confirm/correct loop + accessible UI.
- **Demo:** Offline, speak an unclear/soft phrase → it shows its best-guess clean sentence and reads it back to confirm.
- **Risk note:** Assistive communication aid, not a diagnostic/medical tool.

### 10. Kasa-Kasama — Offline voice companion for isolated / low-mobility users
- **Who:** Housebound, elderly, or low-mobility users who are often alone and want a hands-free, offline conversational companion.
- **What:** Fully voice-driven: the user talks in Taglish → offline STT → a local LLM responds conversationally → on-device TTS speaks back. No typing, no screen needed, no internet. Can also keep simple spoken notes/reminders.
- **Why local:** Companionship/independence must work 24/7 regardless of signal, conversations are intimate and private, and constant cloud chat would be expensive and laggy.
- **The 12h depth:** continuous STT → LLM chat → TTS loop + simple memory of the conversation + fully hands-free flow.
- **Demo:** Offline, hold a short spoken back-and-forth entirely by voice — no keyboard touched.
- **Risk note:** A companion/independence aid for daily life, not therapy or medical care.

---

## My recommendation

- **Strongest "useful + provably local" (go here if unsure):** **Tinig** (live offline captioning) — clear disabled user, obvious why local, and an emotionally strong live demo. Scores hard on the 50% that matters.
- **Most impactful / memorable demo:** **Boses** — giving a non-verbal person a voice offline is the kind of two-way demo judges remember.
- **Easiest of the five, still full 12h:** **Diktado** — STT + format modes + accessible UI, low risk.

All ten put *offline speech recognition at the core* and serve a real **accessibility** user, so your 25% Local AI score is locked in and your Problem&Usefulness story is strong.

---

## Which ideas truly fill a full 12 hours (and which don't)

The risk isn't just "too hard" — it's also "too small." If you finish the core in 4 hours, you'll waste the day or over-polish. These are rated on **12-hour fit**: ✅ fits well (meaty but finishable), ⚠️ risks running over, 🔸 might finish too early (needs scope added to fill 12h).

| # | Idea | Pipeline weight | 12h fit | Note |
|---|------|-----------------|---------|------|
| 1 | **Tinig** | STT + caption cleanup + chunked near-real-time + UI | ✅ **Best fit** | Chunking audio for "live" feel is the meaty part that fills the day |
| 2 | **Boses** | shorthand→sentence LLM + reverse STT + TTS + UI | ✅ **Best fit** | Two directions + TTS = a genuine full day |
| 6 | **Senyas** | bidirectional STT + LLM expand + TTS + split UI | ✅ **Best fit** | Most complete pipeline; realistically a full 12h |
| 8 | **Basa Pa** | simplify LLM + TTS + STT Q&A loop + UI | ✅ Good fit | Speech in AND out gives it real surface |
| 10 | **Kasa-Kasama** | continuous STT→LLM→TTS loop + memory | ✅ Good fit | The hands-free loop + memory fills the time |
| 4 | **Diktado** | STT + multi-format LLM + read-back UI | ✅ Good fit | Add the format modes + read-back to reach 12h |
| 7 | **Alalay** | STT + reminder-structuring LLM + scheduler + UI | ✅ Good fit | The scheduler/step logic adds solid hours |
| 9 | **Tahimik** | STT + reconstruction LLM + confirm loop | ⚠️ Watch scope | Reconstruction quality can eat time; keep the loop simple |
| 3 | **Sigaw** | STT + intent LLM + safe action library | ⚠️ Watch scope | Wiring real OS actions safely can overrun — keep actions few |
| 5 | **Hudyat ng Tahanan** | continuous audio + sound/keyword detect + alert UI | ⚠️ Watch scope | Non-speech sound detection is the risky bit; may need tuning |

### Best picks for "genuinely a 12-hour build, not more, not less"
1. **Senyas** — the most complete pipeline (both directions + TTS + split UI). Realistically fills all 12 hours and demos beautifully.
2. **Boses** — two-way voice bridge; meaty but finishable, high emotional impact.
3. **Tinig** — the near-real-time chunking is exactly the kind of work that fills a day without blowing scope.

### If you want to avoid finishing too early
Any single-direction idea (Diktado, Alalay) can finish in ~6–8h. To honestly fill 12 hours, add one of: a second output mode, read-back TTS, a small accessible-settings panel (font size/contrast/speed), or a conversation-history view. That depth also raises your Product & Demo Quality score (15%).

### If you're worried about running over
Avoid the ⚠️ ones (Sigaw, Hudyat ng Tahanan, Tahimik) unless a teammate has done OS-automation or audio-event detection before. Their risky part isn't the speech — it's the action-wiring or non-speech audio.

---

## How to implement offline speech recognition (the part you asked for)

### Recommended engine: **faster-whisper** (Whisper, running locally)
Confirmed current best offline choice. It's multilingual (handles **Tagalog/Taglish**, which Vosk does poorly), runs fully offline after a one-time model download, and `faster-whisper` is the easiest fast path in Python. (`whisper.cpp` is an alternative if you want C++/GPU on Windows via Vulkan, but faster-whisper is simpler for a 12h build.)

### Step 1 — Install
```bash
pip install faster-whisper sounddevice streamlit
```
`faster-whisper` downloads the model once, then runs offline. `sounddevice` captures mic audio. `streamlit` is your UI.

### Step 2 — Pick a model size (balance speed vs accuracy on your laptop)
- `tiny` / `base` — fastest, fine for short clean Taglish commands, runs on a "potato laptop."
- `small` — best balance for most demos. **Start here.**
- `medium` — more accurate Taglish but slower; only if you have a decent GPU.

> Download the model ONCE while you still have internet (hour 0), then everything runs offline.

### Step 3 — Minimal offline transcription (the core you reuse in every idea)
```python
from faster_whisper import WhisperModel

# Loads locally; downloads once, then fully offline.
# device="cpu" works everywhere; use "cuda" if you have an NVIDIA GPU.
model = WhisperModel("small", device="cpu", compute_type="int8")

def transcribe(audio_path: str) -> str:
    # language="tl" hints Tagalog; drop it to let Whisper auto-detect Taglish.
    segments, _ = model.transcribe(audio_path, language="tl", beam_size=5)
    return " ".join(seg.text for seg in segments).strip()
```

### Step 4 — Record from the mic (for live demos)
```python
import sounddevice as sd
from scipy.io.wavfile import write

def record(seconds=5, path="input.wav", rate=16000):
    print("Recording... speak now.")
    audio = sd.rec(int(seconds * rate), samplerate=rate, channels=1)
    sd.wait()
    write(path, rate, audio)
    return path

text = transcribe(record(5))
print("You said:", text)
```
(`pip install scipy` for the wav writer.)

### Step 5 — Chain it into the local LLM (the second half of your pipeline)
Run a local LLM with **Ollama** and feed it the transcript. Example for Tinig caption cleanup:
```python
import ollama  # pip install ollama ; and install Ollama + `ollama pull llama3.2`

def clean_caption(transcript: str) -> str:
    prompt = f"""Clean up this Taglish speech-to-text into a readable,
properly punctuated caption. Keep it faithful, do not add info.
Text: "{transcript}" """
    resp = ollama.chat(model="llama3.2",
                       messages=[{"role": "user", "content": prompt}])
    return resp["message"]["content"]
```
Swap the prompt per idea: expand shorthand into full sentences (Boses), map-to-intent (Sigaw), format-to-notes (Diktado), detect trigger words (Hudyat ng Tahanan).

### Step 6 — Wrap in Streamlit (single-screen, accessible UI)
```python
import streamlit as st

st.title("Tinig — Offline Live Captions")
# Big, high-contrast text matters for an accessibility tool.
if st.button("🎤 Listen (5s)"):
    text = transcribe(record(5))
    st.markdown(f"## {clean_caption(text)}")  # large caption output
```
Run with `streamlit run app.py`. For accessibility, use large fonts, high contrast, and clear buttons.

### Step 7 — PROVE it's offline (this wins the demo)
- Download Whisper model + `ollama pull` **before** you go offline.
- During the demo, **turn off WiFi** and open a network monitor (e.g., Windows Resource Monitor → Network) to show zero traffic while it transcribes.
- That single move nails Technical Execution (20%) + Demo Quality (15%) and answers the mandatory "why local" question visually.

### Gotchas to handle in your 12 hours
- **Model download time** — do it in hour 0 while online. This is the #1 thing that bites teams.
- **Mic permissions / device index** — test `sounddevice` early; set the right input device.
- **Taglish accuracy** — try `small` and omit `language=` to let it auto-detect code-switching; always keep a **text-input fallback** so a bad mic moment can't kill your demo.
- **Latency** — use `int8` compute and the smallest model that's accurate enough; keep clips short (5–10s) for live demos.

---

## Suggested 12-hour timeline (speech build)

| Time | Goal |
|------|------|
| 0:00–1:00 | Install everything, **download Whisper model + Ollama model while online**, confirm transcription works OFFLINE. |
| 1:00–3:00 | Nail the core transcribe() on real Taglish samples; pick model size. |
| 3:00–5:00 | Build the second step (parse/critique/format/intent/narrate) with the local LLM. |
| 5:00–6:00 | Break + cut scope to one clean flow. |
| 6:00–9:00 | Streamlit UI: record button → transcript → result. Add text fallback. |
| 9:00–10:30 | Error handling, sample inputs, verify fully offline with network monitor. |
| 10:30–11:15 | Record ~1-min demo video (pull the plug), write README with the "why local" answer + disclosures. |
| 11:15–12:00 | Public GitHub repo, submit on Cerebral Valley, post X/LinkedIn video with #AppBuildersPH. |

---

*Engine choice verified Oct 2026: faster-whisper / whisper.cpp are the current best fully-offline STT; Whisper handles Taglish where Vosk does not. Scoped for AppBuilders PH Hackathon 2026 (Local AI). Submission freezes 10:00 AM, Oct 10 — no extensions.*
