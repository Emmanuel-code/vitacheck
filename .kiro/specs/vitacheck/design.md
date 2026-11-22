# VitaCheck — design (starter; to be refined in Kiro)

## Architecture
- Frontend: Next.js (App Router) + TypeScript, PWA, mobile-first.
- Backend: Firebase — Firestore (readings), Auth (anonymous), App Check (debug token in dev),
  AI Logic (Gemini Nano on-device + Gemini Flash cloud).
- Hosting: Vercel.

## Data model (Firestore)
- `users/{uid}` — anonymous user doc (created on first use).
- `users/{uid}/readings/{readingId}` — { type: "bp" | "glucose", systolic?, diastolic?, pulse?,
  value?, fasting?, takenAt, classification, summary, source: "on-device" | "cloud" }.

## Hybrid routing
- Nano first for instant classification of a single reading (fast, private, offline).
- Cloud (Flash) for weekly trends, plans, Q&A (needs network; falls back to a clear message offline).
- Every AI response is labelled with its source badge.

## Safety
- No diagnosis, no prescriptions. Disclaimer on every AI answer. Red flags → clinic prompt.
