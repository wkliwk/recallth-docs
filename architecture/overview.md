# Recallth — Architecture Overview

## Repo Map

```
wkliwk/
├── recallth-backend      Express 5 + TypeScript + MongoDB   API + AI logic
├── recallth-mobile       Expo / React Native                 Primary mobile app
├── recallth-web          Next.js                             Web app
├── recallth              React + Vite                        Original frontend (legacy)
└── recallth-docs         Markdown                            This repo
```

## Infrastructure

| Layer | Service |
|---|---|
| API | Fly.io (`recallth-backend.fly.dev`) |
| Database | MongoDB Atlas (M0 free tier) |
| Mobile | Expo / EAS Build |
| Web | Vercel (auto-deploy from `main`) |
| AI | Google Gemini API (backend) |

## Backend Structure

```
recallth-backend/src/
├── config/           DB connection, env config
├── middleware/       Auth (JWT), error handling
├── models/           Mongoose schemas
│   ├── User.ts
│   ├── HealthProfile.ts
│   ├── CabinetItem.ts
│   ├── BloodworkEntry.ts
│   ├── BodyStatEntry.ts
│   ├── DoseLog.ts / DailyLog.ts / IntakeLog.ts
│   ├── Conversation.ts
│   ├── WeeklyDigest.ts / InsightCache.ts
│   ├── GoalCheckIn.ts
│   ├── SideEffect.ts
│   ├── FamilyMember.ts
│   ├── SharedStack.ts
│   ├── ExtractionReview.ts
│   └── UserSettings.ts
├── routes/           REST endpoints (one file per domain)
│   ├── auth.ts / authGoogle.ts
│   ├── cabinet.ts        ← core feature (largest file)
│   ├── bloodwork.ts
│   ├── bodyStats.ts
│   ├── chat.ts
│   ├── digest.ts
│   ├── export.ts
│   ├── extractionReview.ts
│   ├── familyMembers.ts
│   ├── goals.ts
│   ├── history.ts
│   ├── insights.ts
│   ├── intake.ts
│   ├── interactions.ts
│   ├── journal.ts
│   ├── profile.ts
│   ├── schedule.ts
│   ├── settings.ts
│   ├── sideEffects.ts
│   └── wellness.ts
├── services/         AI service wrappers, business logic
└── utils/            Helpers
```

## Auth Flow

1. Email/password → JWT issued by `/auth/login`
2. Google OAuth → `/auth/google` → JWT issued
3. All protected routes require `Authorization: Bearer <token>`

## API Base URL

- Production: `https://recallth-backend.fly.dev`
- Local: `http://localhost:4000`

## Planned Additions

- `src/routes/nutrition.ts` — Nutrition Tracker endpoints (see [Epic #109](https://github.com/wkliwk/recallth-backend/issues/109))
- `src/models/MealEntry.ts`, `NutritionCategory.ts`, `DailyNutritionSummary.ts`
