# PS-164 PQC Readiness Scanner — Streamlit Deployment Package

Cleaned deployment package extracted from the supplied project ZIP.

## Entry point

`app.py`

## Local run

Use Python 3.12 for a close match to the current Streamlit Community Cloud default.

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
streamlit run app.py
```

## GitHub push

Create an empty GitHub repository first, then run these commands from this folder:

```powershell
git init
git branch -M main
git add .
git commit -m "Prepare PS-164 scanner for Streamlit Cloud"
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

## Streamlit Community Cloud

Create the app from the GitHub repository and choose:

- Branch: `main`
- Main file: `app.py`
- Python: `3.12` in Advanced settings

The web app supports ZIP repository uploads and individual asset uploads. The native local-folder picker is for local testing only.

Docker image scanning requires a Docker daemon/CLI, so that feature is intended for an environment where Docker is actually available.
