# FitFlow Redesign — Tech Stack Summary

## Frontend: Flutter
Chosen for a single codebase across iOS/Android/Web, near-native performance
(Skia/Impeller), strong AI/ML plugin support (TFLite, ML Kit), and the lowest
long-term maintenance cost for a mid-sized team.

## Backend: Next.js / NestJS + FastAPI (hybrid)
- Next.js/NestJS handles the core API layer — Auth, Workout, Nutrition,
  Community services, and real-time traffic.
- FastAPI (Python) runs as a decoupled AI microservice for personalized
  plans and computer-vision nutrition logging, since Python has the
  strongest AI/ML ecosystem (TensorFlow, PyTorch, scikit-learn).

## Database: PostgreSQL (via Supabase)
Relational structure fits Users/Workouts/Progress/Meals/Community data.
Supports Row-Level Security for GDPR/CCPA compliance and integrates
natively with Supabase Auth and Realtime.

## Authentication: Supabase Auth
Uses the same Postgres database as the rest of the stack, integrates
directly with Row-Level Security, and is the most cost-effective option
for a mid-sized team.

## Real-time layer: Supabase Realtime / WebSockets
Pushes live updates (progress, community, challenges) to the Flutter client.

## Cache: Redis
Session data, rate-limiting, and hot-read caching for the backend API.

## Justification summary
This stack was selected using the weighted decision matrix in
`comparison-matrix.md` — every layer scored highest or tied-highest in its
category, and Auth, database, and real-time all live under one provider
(Supabase), reducing integration overhead for a startup-sized team.