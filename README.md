# Polymarket Trend Analyzer

Full-stack application for detecting Polymarket prediction market trend reversals and generating AI-powered content.

## Stack

**Backend:** Python FastAPI + SQLAlchemy + SQLite
**Frontend:** Vue.js (Sprint 5+)
**LLM:** OpenAI API → Google Gemini
**Database:** SQLite (dev) → PostgreSQL (prod)

## Features

- 🔍 Trend reversal detection algorithm
- 📊 Tag-based market monitoring
- 📝 AI content generation (articles, summaries, SEO)
- ✅ Admin validation workflow
- 🔐 Authentication (fake auth → Google OAuth)
- 📅 Post scheduling system

## Quick Start

### Backend Setup

1. **Install dependencies:**
```bash
cd backend
pip install -r requirements.txt
```

2. **Initialize database:**
```bash
python -m app.database.seed
```

3. **Create .env file:**
```bash
cp .env.example .env
# Edit .env and add your API keys
```

4. **Run server:**
```bash
uvicorn app.main:app --reload
```

Server: http://localhost:8000
API Docs: http://localhost:8000/docs

### Frontend (Legacy - TypeScript)

```bash
cd frontend
npm install
npm run build
```

**Note:** Vue.js frontend coming in Sprint 5.

## Project Status

- ✅ **Sprint 1:** Backend foundation complete (layered architecture, SQLite, fake auth)
- 🚧 **Sprint 2:** Polymarket API integration (in progress)
- ⏳ **Sprint 3:** OpenAI content generation
- ⏳ **Sprint 4:** Admin API endpoints
- ⏳ **Sprint 5:** Vue.js dashboard
- ⏳ **Sprint 6:** Validation interface
- ⏳ **Sprint 7:** Testing & polish

## API Endpoints

### Public
- `GET /` - API documentation
- `GET /health` - Health check
- `GET /reversal-trends` - Legacy endpoint
- `GET /api/reversal-trends` - Trend reversals
- `GET /api/tags` - List monitored tags
- `GET /api/questions/raw` - All questions
- `GET /api/questions/filtered` - Questions with reversals

### Authenticated (Bearer token)
- `POST /api/tags` - Create tag
- `DELETE /api/tags/{id}` - Delete tag (admin only)

### Admin Only
- `GET /api/validation-queue` - Pending posts
- `POST /api/validation-queue/{id}/approve` - Approve post
- `POST /api/validation-queue/{id}/reject` - Reject post
- `POST /api/validation-queue/{id}/schedule` - Schedule post

## Testing

See [backend/TESTING.md](backend/TESTING.md) for detailed testing guide.

**Fake auth tokens:**
- Admin: `Authorization: Bearer admin-token`
- User: `Authorization: Bearer user-token`

## Documentation

- [Sprint 1 Summary](docs/sprint1-summary.md)
- [Vision](specs/00-vision.md)
- [Product Spec](specs/01-product-spec.md)
- [Architecture](specs/02-architecture.md)
- [Engineering Spec](specs/03-engineering-spec.md)
- [Coding Rules](specs/04-coding-rules.md)
- [Roadmap](specs/05-roadmap.md)
