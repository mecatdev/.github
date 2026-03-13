# Mecat [REPORT ARE ON THIS REPO]

Investors should not wait for founder schedules. Founders should not repeat the same pitch fifty times.

Mecat is an AI-powered investment marketplace where each startup has a digital business avatar that can answer investor questions in real time using business-specific context.

## Report
**Hackathon Submission Report:** [Welcome To The Jungle (PDF)](../Report_WelcomeToTheJungle.pdf)

## Why This Project

Built in hackathon spirit: ship fast, prove value, and make due diligence feel instant.

Mecat helps:
- Founders present their business clearly and consistently.
- Investors run faster first-pass due diligence.
- Both sides move from discovery to decision with less friction.

## Core Features

- AI business profiles with structured startup data.
- Real-time investor Q&A powered by Gemini.
- Voice-assisted interaction with transcript flow.
- Knowledge ingestion and retrieval for context-grounded responses.
- Risk and legal analysis workflows.
- Deal and conversation tracking.

## Tech Stack

- Frontend: Next.js, TypeScript, Tailwind CSS
- Backend: Node.js, Express, TypeScript
- Database: PostgreSQL + pgvector
- ORM: Prisma
- AI: Gemini API
- Auth: Clerk

## Project Structure

```text
mecat/
  backend/   # API, Prisma schema/migrations, business logic
  frontend/  # Next.js app, UI, hooks, API integrations
```

## Quick Start

### 1. Backend

```bash
cd backend
npm install
cp .env.example .env
# Fill required values in .env (DATABASE_URL, GEMINI_API_KEY, Clerk keys)
npm run db:generate
npm run db:migrate
npm run db:seed
npm run dev
```

Backend runs at `http://localhost:4000`.

### 2. Frontend

```bash
cd frontend
npm install
cp .env.example .env
# Set NEXT_PUBLIC_BACKEND_URL=http://localhost:4000
npm run dev
```

Frontend runs at `http://localhost:3000`.

## Docker (Optional)

### Backend + Postgres

```bash
cd backend
cp .env.example .env
docker compose up -d --build
docker compose exec backend npm run db:seed
```

### Frontend

```bash
cd frontend
cp .env.example .env
docker compose up -d --build
```

## API Snapshot

- `GET /api/businesses`
- `GET /api/businesses/:idOrSlug`
- `POST /api/conversations/:businessId/messages`
- `POST /api/voice/*`
- `POST /api/knowledge/*`
- `GET /api/health`

## Notes for Local Tunneling

If frontend is exposed via tunnel (for cross-device voice testing), backend must also be reachable from that device. Set:
- `frontend/.env` -> `NEXT_PUBLIC_BACKEND_URL=<public-backend-url>`
- `backend/.env` -> `CORS_ORIGIN=<public-frontend-url>`

Then restart both services.

## Vision

Mecat is a foundation for AI-native fundraising workflows: always-on investor conversations, contextual responses, and faster founder-investor matching.
