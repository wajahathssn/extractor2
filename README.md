# Scientific Literature → JSON Extractor (Experimental)

✅ Live site: https://wajahathssn.github.io/  
🧪 Experimental version for **2-shot extraction**, **qualifier/context capture**, and **RAG testing**

This repo hosts an experimental web UI (GitHub Pages) + backend API (Vercel) for extracting structured JSON from scientific PDFs.

Compared to the baseline version, this repo is where new features are tested, including:
- **Two-shot extraction** (extract → verify/fix)
- **Qualifier/context fields** (e.g., conditions, device context, additives, temperatures)
- **RAG experiments** (retrieve relevant chunks instead of sending the whole paper)

---

## Current workflow
1. Open the live site.
2. Upload a PDF.
3. Load the PDF text in the browser.
4. Enter your extraction instruction.
5. Choose a provider/model (OpenAI, Claude, Gemini, DeepSeek).
6. Run extraction.
7. Copy or download the JSON output.

---

## Planned experimental features
- [ ] **Two-shot mode** (candidate extraction + verification pass)
- [ ] **Qualifier-aware schema** (conditions / context per claim)
- [ ] **RAG test modes**
  - Full text (baseline)
  - Keyword retrieval (RAG-lite)
  - Embedding retrieval (semantic RAG)
- [ ] **Section-aware extraction** (Abstract / Full paper)

---

## Repository structure
- `index.html` — frontend UI (GitHub Pages)
- `backend/` — Vercel backend API
  - `api/extract_json.js` — main extraction endpoint
  - `api/health.js` — health check
  - `package.json` — backend dependencies
  - `vercel.json` — Vercel config
  - `.env.example` — environment variable template

---

## Backend setup (Vercel)
This project expects the backend to be deployed on Vercel with the root directory set to `backend`.

### Required environment variables
Set these in **Vercel → Project Settings → Environment Variables**:

- `OPENAI_API_KEY`
- `ANTHROPIC_API_KEY`
- `GEMINI_API_KEY`
- `DEEPSEEK_API_KEY`

Optional:
- `API_AUTH_KEY` (shared key if you want to protect the API endpoint)

---

## Frontend setup (GitHub Pages)
The frontend is a single `index.html` file hosted on GitHub Pages.

Update the backend URL by editing `API_BASE` inside `index.html`:

```js
const API_BASE = "https://YOUR-VERCEL-PROJECT.vercel.app/api";
