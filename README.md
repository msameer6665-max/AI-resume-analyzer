# 📄 ATS Resume Checker

A Streamlit app that scores a resume for ATS (Applicant Tracking System) friendliness and suggests concrete improvements, powered by Google Gemini Flash.

## Features
- Upload a resume as **PDF, DOCX or TXT**
- Optional **job description** for a tailored score and keyword-gap analysis
- **ATS score (0-100)** with a 5-category breakdown
- Strengths, missing keywords and prioritised (High/Medium/Low) improvements with example rewrites
- Download the report as Markdown

> The score is an AI-generated estimate, not the output of a real ATS. Use it as guidance.

## Project structure
```
ats-resume-checker/
├── app.py
├── requirements.txt
└── README.md
```

## Run locally
1. Get a free Gemini API key: https://aistudio.google.com/apikey
2. Install and run:
   ```bash
   python -m venv venv
   source venv/bin/activate        # Windows: venv\Scripts\activate
   pip install -r requirements.txt
   streamlit run app.py
   ```
3. Provide the API key in **one** of these ways:
   - paste it into the sidebar field in the app, or
   - set an environment variable: `export GEMINI_API_KEY="your-key"` (Windows PowerShell: `$env:GEMINI_API_KEY="your-key"`), or
   - create `.streamlit/secrets.toml` containing `GEMINI_API_KEY = "your-key"`

## Choosing the Gemini model
The default is `gemini-2.5-flash`. You can type any other Gemini model name (e.g. a newer Flash release) in the sidebar, or change `DEFAULT_MODEL` in `app.py`.

## Push to GitHub (using the website only)
1. Sign in at https://github.com and click **+ → New repository**.
2. Name it `ats-resume-checker`, choose **Public** (required for the free Streamlit Cloud tier unless you link a private repo), and click **Create repository**.
3. On the new repo page click **uploading an existing file**.
4. Drag in `app.py`, `requirements.txt` and `README.md`, then click **Commit changes**.
5. **Never upload your API key or a `secrets.toml` file.**

## Deploy on Streamlit Community Cloud
1. Go to https://share.streamlit.io and sign in with GitHub (authorise access to your repo when asked).
2. Click **Create app** → **Deploy a public app from GitHub**.
3. Choose your repository, branch `main`, and main file path `app.py`.
4. Open **Advanced settings → Secrets** and paste:
   ```toml
   GEMINI_API_KEY = "your-key-here"
   ```
5. Click **Deploy**. After a minute or two you'll get a public URL like `https://your-app-name.streamlit.app`.

To update the app later, edit the file on GitHub (pencil icon → **Commit changes**); Streamlit redeploys automatically.

## Troubleshooting
- **"Very little text could be extracted"** - the PDF is probably a scanned image. Export a text-based PDF or a DOCX.
- **"Analysis failed" / API key errors** - check the key and that the model name exists for your account.
- **429 / quota errors** - the free tier has rate limits; wait a minute and retry.
- **Privacy** - resume text is sent to Google's Gemini API. Don't use it for resumes you don't have permission to process.
