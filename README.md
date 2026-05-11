# AI-TEXT-BASED-SUMMARIZER
A web based AI tool that summarizes text and pdf documents instantly using Google's Gemini API 

---

## PROBLEM STATEMENT
Reading long documents, research papers, or articles takes significant time. This tool helps users quickly extract the ke points from any text or PDF without reading the entire content - saving time and improving productivity.

---

## Objective

To build a full-stack AI-powered summarization tool that accepts raw text
or PDF files and returns a concise, accurate summary using a large language model.

---

## Tech Stack

| Component | Technology |
|---|---|
| Backend | Python, FastAPI |
| AI Model | Google Gemini 2.5 Flash |
| PDF Extraction | PyMuPDF (fitz) |
| Tunneling | ngrok |
| Frontend | HTML, CSS, JavaScript |

---

## Why Gemini API

During development, HuggingFace Transformers was initially considered
for the summarization model. However, version conflicts in the Colab
environment (Transformers 5.0.0 dropping the summarization pipeline)
made it unreliable. Gemini API was chosen as an alternative because
it is easy to integrate, requires no local model downloads, and
produces high quality summaries out of the box.

---

## Project Structure

---

## How to Run

### Step 1 — Get API Keys
- Gemini API key: [aistudio.google.com](https://aistudio.google.com)
- ngrok authtoken: [dashboard.ngrok.com](https://dashboard.ngrok.com)

### Step 2 — Backend (Google Colab)
1. Open a new Google Colab notebook
2. Run this in the first cell:
3. Paste the backend code into the next cell
4. Replace `GEMINI_API_KEY` and `NGROK_AUTH_TOKEN` with your actual keys
5. Run the cell — copy the ngrok public URL from the output

### Step 3 — Frontend
1. Open `index.html` in a text editor
2. Update `API_URL` with your ngrok URL from Step 2
3. Open `index.html` in any browser

---

## API Endpoints

| Endpoint | Method | Input | Output |
|---|---|---|---|
| `/` | GET | None | API status check |
| `/summarize/text` | POST | JSON: `text`, `length` | AI summary of text |
| `/summarize/pdf` | POST | PDF file + `length` | AI summary of PDF |

### Summary Length Options
- `short` — 2 to 3 sentences
- `medium` — 4 to 5 sentences  
- `long` — 7 to 8 sentences

---

## Limitations

- The Colab session times out after inactivity — backend goes down if Colab disconnects
- The ngrok URL changes every time the Colab session restarts — must update `API_URL` in index.html each time

---

## Future Improvements

- Support for additional file formats such as Word (.docx) and Excel (.xlsx)
- URL-based summarization — paste a website link and summarize its content
- Save summary history so users can revisit past results

---

## Results

The application successfully summarizes both plain text and PDF documents.
It supports three summary lengths and handles errors such as empty input,
files that are too short, and non-PDF uploads gracefully.
