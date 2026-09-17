# ADR-001: Adopt Flutter + Next.js + FastAPI + Supabase stack

## Status
Accepted

## Context
FitFlow needs a single codebase across iOS/Android/Web, an AI microservice
for personalized plans and computer-vision nutrition logging, real-time
social features, and GDPR/CCPA-compliant health-data storage, to be built
by a mid-sized team on a startup budget.

## Decision
- Flutter for the client (iOS/Android/Web)
- Next.js/NestJS for the core API layer
- A decoupled FastAPI microservice for AI/ML
- PostgreSQL via Supabase for storage
- Supabase Auth for identity
- Supabase Realtime/WebSockets for live features
- Redis for caching hot data

## Consequences

### Positive
- A single frontend codebase cuts development and maintenance cost.
- Postgres, Auth, and Realtime under one provider (Supabase) reduce
  integration overhead and vendor count.
- FastAPI isolates AI compute so it can scale independently of the main API.

### Negative
- Introduces two backend languages (TypeScript and Python) to maintain.
- Some reliance on Supabase as a managed platform, mitigated since
  Postgres and Auth are built on portable, open standards.