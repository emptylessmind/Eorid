# Eorid

Eorid is a cross-platform social + AI companion platform: a web app, mobile apps
(iOS/Android), desktop apps (Windows/macOS/Linux), and support for ARM-based
devices — built around a personal, on-device AI that adapts to each user, plus
Instagram-style social features (posts, follow/following, chat, friends).

This repo is the starting scaffold. It is intentionally minimal — a skeleton
to build out feature by feature, not a finished product.

## Repo layout

```
eorid-starter/
├── web/                 Next.js web app (deployed to Vercel)
│   └── app/             App Router pages
├── docs/
│   └── ai-memory-schema.json   Draft schema for the portable AI memory/persona file
└── README.md
```

## Core design decisions (so far)

- **Stack**: Next.js (web) on Vercel, Firebase (Auth + Firestore + Storage) for
  identity, social graph, posts, and chat.
- **AI runs on-device**, model-agnostic via GGUF + a llama.cpp-based runtime.
  Users pick any compatible model themselves — nothing is bundled or hosted by
  the platform.
- **Personalization = a memory/context file**, not fine-tuned weights. This
  keeps it small, portable across different models, and exportable/importable
  so users can share or transfer their AI's "personality" with others. See
  `docs/ai-memory-schema.json`.
- **Uniqueness per user** comes from four layers: model choice, persona setup
  at onboarding, emergent memory from usage, and per-user permission settings.

## Getting started (web)

```bash
cd web
npm install
npm run dev
```

## Status

Early scaffold. Auth, posts, follow graph, chat, and the on-device AI runtime
are not yet implemented — this repo currently only holds the landing page
shell and the draft memory schema.
