# Recallth — Product Documentation

## Overview

**Recallth** is an AI-powered personal health advisor focused on supplement management. It helps users track their supplements, understand interactions, log health data, and get personalised AI-driven insights.

**Target users:** Health-conscious individuals managing supplements, vitamins, and medications — from gym-goers to patients with chronic conditions.

**Core problem it solves:** Supplement and health tracking is scattered across multiple apps, spreadsheets, and memory. Recallth centralises everything and adds AI intelligence on top.

---

## Repos

| Repo | Stack | Purpose |
|---|---|---|
| [recallth-backend](https://github.com/wkliwk/recallth-backend) | Express 5 + TypeScript + MongoDB | API, data models, AI logic |
| [recallth-mobile](https://github.com/wkliwk/recallth-mobile) | Expo / React Native | Primary mobile app |
| [recallth-web](https://github.com/wkliwk/recallth-web) | Next.js | Web app |
| [recallth](https://github.com/wkliwk/recallth) | React + Vite | Original frontend (legacy) |
| [recallth-docs](https://github.com/wkliwk/recallth-docs) | Markdown | This repo — product docs |

---

## Features

### 1. Supplement Cabinet (藥箱)

**Description:** The core feature. Users build a personal cabinet of supplements, vitamins, and medications. AI helps search, identify, and manage items.

**User flow:**
1. Search for a supplement by name or description (AI-powered search)
2. Add to cabinet with dose, frequency, and notes
3. View all cabinet items with status (active/paused/stopped)
4. AI checks for interactions between items

**Acceptance criteria:**
- [ ] Add supplement by name (AI identifies and pre-fills details)
- [ ] Edit dose, frequency, notes
- [ ] Mark as active / paused / stopped
- [ ] Interaction checker flags conflicts between cabinet items
- [ ] Cabinet items persist across sessions

---

### 2. AI Chat Advisor

**Description:** Conversational AI that answers health and supplement questions using the user's personal health context (profile, cabinet, bloodwork, goals).

**User flow:**
1. User asks a question in natural language
2. AI responds with personalised advice based on their health data
3. Conversation history is saved per session

**Acceptance criteria:**
- [ ] AI has access to user's cabinet, bloodwork, profile, goals
- [ ] Responses are contextually personalised
- [ ] Conversation history saved and resumable

---

### 3. Bloodwork Tracking

**Description:** Users upload or manually enter blood test results. AI interprets results in the context of their supplements and health goals.

**User flow:**
1. Upload blood test report (PDF/image) or enter values manually
2. AI extracts and parses values
3. User reviews and confirms extracted data
4. AI flags out-of-range values and links to supplement recommendations

**Acceptance criteria:**
- [ ] Upload and parse bloodwork documents (extraction review flow)
- [ ] Manual entry of individual markers
- [ ] Historical trend view per marker
- [ ] AI commentary on results in chat context

---

### 4. Health Profile

**Description:** User's personal health record — age, weight, height, conditions, allergies, goals.

**User flow:**
1. Fill in profile during onboarding
2. Update any time from Settings
3. Profile informs all AI responses

**Acceptance criteria:**
- [ ] Basic demographics (age, sex, weight, height)
- [ ] Health conditions and allergies
- [ ] Profile used as AI context in all features

---

### 5. Body Stats Tracking

**Description:** Log body measurements over time (weight, body fat %, etc.).

**User flow:**
1. Log a measurement with date
2. View trend chart

**Acceptance criteria:**
- [ ] Log weight and other body stats with date
- [ ] Trend chart across time

---

### 6. Supplement Schedule & Dose Logging

**Description:** Set dosing schedules for cabinet items. Log when doses are taken.

**User flow:**
1. Set schedule for a cabinet item (morning / evening / with food)
2. Daily check-in to log doses taken
3. View adherence history

**Acceptance criteria:**
- [ ] Set schedule per cabinet item
- [ ] Daily dose logging
- [ ] Adherence history

---

### 7. Weekly Digest

**Description:** AI-generated weekly summary of the user's health data, supplement adherence, and personalised insights.

**Acceptance criteria:**
- [ ] Auto-generated weekly (or on-demand)
- [ ] Covers: supplement adherence, bloodwork trends, AI highlights

---

### 8. Goals

**Description:** Users set health goals (e.g. "improve sleep", "build muscle"). AI tracks progress and links recommendations to goals.

**Acceptance criteria:**
- [ ] Create and manage goals
- [ ] Goal check-ins
- [ ] AI references goals in chat and insights

---

### 9. Side Effects Logging

**Description:** Users log side effects they experience. AI correlates with their supplement stack.

**Acceptance criteria:**
- [ ] Log side effect with date and severity
- [ ] AI analysis linking side effects to possible supplement causes

---

### 10. Family Members

**Description:** Manage health profiles for family members (e.g. parents, children).

**Acceptance criteria:**
- [ ] Add family member profiles
- [ ] Switch context to manage a family member's data

---

### 11. Insights

**Description:** AI-generated health insights based on all available user data.

**Acceptance criteria:**
- [ ] Insights generated from combined data sources
- [ ] Actionable recommendations with references to cabinet items

---

### 12. Export

**Description:** Export health data in structured formats (PDF, CSV).

**Acceptance criteria:**
- [ ] Export bloodwork history
- [ ] Export supplement cabinet
- [ ] Export as PDF or CSV

---

### 13. Journal

**Description:** Personal health journal with free-form notes.

**Acceptance criteria:**
- [ ] Create and edit journal entries with date
- [ ] Searchable entries

---

### 14. Nutrition Tracker — 營養追蹤 (Planned)

**Status:** Backlog — see [Epic #109](https://github.com/wkliwk/recallth-backend/issues/109) and [nutrition-tracker-feature.md](./nutrition-tracker-feature.md)

**Description:** Track daily food intake via AI natural language input. Creates a supplement ↔ nutrition closed loop: nutrient gaps automatically trigger cabinet supplement recommendations.

**Why this is the moat:** No competitor combines food nutrition tracking with supplement cabinet recommendations. recallth will be the only app that says "you're short 70g protein today → your Whey Protein can fill that gap."

---

## Out of Scope (MVP)

- Full meal planning / recipe suggestions
- Pharmacy / prescription management
- Wearable device integrations (Apple Watch, Fitbit)
- Social / community features
- Telemedicine / doctor consultations

---

## Auth

- Email + password
- Google OAuth
- JWT-based sessions
