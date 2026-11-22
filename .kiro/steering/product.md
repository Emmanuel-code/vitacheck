# VitaCheck — product steering

VitaCheck is a BP & diabetes wellness companion web app (Next.js + TypeScript PWA).
A person logs blood pressure and blood sugar readings; an AI companion explains them
in plain language, flags what needs a clinic visit, and builds a weekly plan.

Hybrid AI (the core of the product):
- On-device first: Gemini Nano via Firebase AI Logic classifies each reading
  (normal / elevated / high) and gives a one-line plain-language summary, offline.
- Cloud when needed: Gemini Flash does weekly trend analysis, meal/activity plans,
  and nurse-style Q&A.
- The UI always shows which path answered: a visible "On-device" badge vs "Cloud" badge.

Safety (non-negotiable):
- The app NEVER diagnoses or prescribes.
- Every AI answer carries: "Educational information only, not medical advice — see a clinician."
- Red-flag logic points to a clinic, never to a treatment decision.

Stack: Next.js + TypeScript, Firebase (AI Logic, Firestore, Auth anonymous, App Check
debug token for dev), deployed on Vercel.
