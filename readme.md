# Product Review Sentiment Scraper API

A FastAPI backend for scraping product reviews, analyzing their sentiment, and saving results to Google Sheets. Designed for easy deployment on platforms like Railway, Render, and PythonAnywhere.

## Features

- REST API built with FastAPI
- Sentiment analysis using TextBlob
- Google Sheets integration for saving review data
- CORS support for frontend integration
- Docker and Railway deployment ready

## Endpoints

- `GET /` — API root/info
- `GET /health` — Health check
- `POST /scrape` — Scrape and analyze reviews (accepts `{ "product_url": "..." }`)

## Setup

### 1. Clone the repository

```sh
git clone <your-repo-url>
cd backend
```

### 2. Install dependencies

```sh
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Google Sheets Credentials

- Place your Google service account credentials in `credentials.json` (see `.gitignore` for security).
- Or set the `GOOGLE_CREDENTIALS_JSON` environment variable with the JSON content.

### 4. Run locally

```sh
uvicorn main:app --reload
```

The API will be available at `http://localhost:8000`.

### 5. Docker

Build and run with Docker:

```sh
docker build -t review-scraper-backend .
docker run -p 8000:8000 review-scraper-backend
```

## Deployment

- **Railway**: Uses [railway.yml](railway.yml) and [Dockerfile](Dockerfile)
- **Render**: Compatible with Procfile and Dockerfile
- **PythonAnywhere**: Uses [wsgi.py](wsgi.py)

## Environment Variables

- `GOOGLE_CREDENTIALS_FILE` — Path to credentials file (default: `credentials.json`)
- `GOOGLE_CREDENTIALS_JSON` — Credentials JSON string (for cloud deployment)
- `GOOGLE_SHEET_NAME` — Name of the Google Sheet (default: "Product Reviews Sentiment Analysis")
- `USER_EMAIL` — Email to share the sheet with (optional)
- `PORT` — Port to run the server (default: 8000)

## Project Structure

```
.
├── main.py
├── requirements.txt
├── Dockerfile
├── railway.yml
├── Procfile
├── wsgi.py
├── credentials.json
├── .env
├── .gitignore
└── readme.md
```

## License

MIT License

---

**Note:** Do not commit your `credentials.json` to version control.
