# Medisum AI — Medical Report Summarizer

Medisum AI is a Flask web application that analyzes and summarizes medical reports. Upload a PDF or TXT file and get an AI-powered summary, severity score, doctor recommendations, and access to a medical chatbot.

---

## Features

- **Report Upload** — Accepts `.pdf` and `.txt` medical documents
- **AI Summarization** — Generates concise summaries of medical findings
- **Severity Analysis** — Classifies report severity as Low, Moderate, or High
- **Entity Extraction** — Detects medical conditions (e.g., fever, diabetes, cancer)
- **Doctor Recommendations** — Suggests relevant medical specialties based on findings
- **Medical Chatbot** — Powered by Google Gemini for medical Q&A
- **Report History** — Stores and retrieves previous analyses
- **Dashboard** — Visual analytics showing severity distribution across reports

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Python 3.10 · Flask |
| Database | SQLite |
| PDF Parsing | pdfplumber |
| AI / LLM | Google Generative AI (Gemini) |
| Image Processing | Pillow |
| Production Server | Gunicorn |
| Deployment | Heroku |

---

## Project Structure

```
medisum-ai/
├── app.py                  # Main Flask app — routes and request handling
├── db.py                   # SQLite database setup and queries
├── utils/
│   ├── summarizer.py       # Text summarization, keyword extraction, severity scoring
│   ├── chatbot.py          # Gemini API chatbot integration
│   └── analytics.py        # Severity statistics for the dashboard
├── templates/              # Jinja2 HTML templates
│   ├── index.html
│   ├── upload.html
│   ├── chatbot.html
│   ├── history.html
│   ├── dashboard.html
│   └── about.html
├── static/                 # CSS and JavaScript assets
├── medisum.db              # SQLite database (auto-created on first run)
├── Procfile                # Heroku deployment command
└── requirements.txt        # Python dependencies
```

---

## Getting Started

### Prerequisites

- Python 3.10+
- A Google Generative AI (Gemini) API key — get one at [Google AI Studio](https://aistudio.google.com/)

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/medisum-ai.git
cd medisum-ai

# Create and activate a virtual environment
python -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # macOS / Linux

# Install dependencies
pip install -r requirements.txt
```

### Configuration

Open `utils/chatbot.py` and replace the placeholder with your API key:

```python
GOOGLE_API_KEY = "YOUR_API_KEY"   # replace with your actual key
```

Or set it as an environment variable and read it with `os.getenv("GOOGLE_API_KEY")`.

### Run Locally

```bash
python app.py
```

The app will be available at `http://127.0.0.1:5000`.

---

## Deployment (Heroku)

```bash
heroku create your-app-name
heroku config:set GOOGLE_API_KEY=your_key_here
git push heroku main
```

The `Procfile` already contains the correct startup command:

```
web: gunicorn app:app
```

---

## Usage

1. Go to the **Upload** page and submit a medical report (PDF or TXT).
2. View the generated **summary**, extracted conditions, and **severity score**.
3. Check the **recommended specialist** based on the analysis.
4. Use the **Chatbot** to ask follow-up medical questions.
5. Browse previous reports in **History** or view aggregate stats on the **Dashboard**.

---

## License

This project is for educational purposes. Medical information provided by this tool is not a substitute for professional medical advice.
