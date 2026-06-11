# 🤖 AI-Powered Interview Preparation Platform

![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React.js-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Gemini AI](https://img.shields.io/badge/Gemini_AI-4285F4?style=for-the-badge&logo=google&logoColor=white)
![Users](https://img.shields.io/badge/Active_Users-20%2B-brightgreen?style=for-the-badge)

> A **Gemini AI-powered mock interview platform** that generates dynamic, role-specific questions and delivers structured performance feedback — with session analytics to track your progress over time.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Live Demo](#live-demo)
- [Tech Stack](#tech-stack)
- [Key Features](#key-features)
- [How It Works](#how-it-works)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [API Reference](#api-reference)
- [Project Structure](#project-structure)
- [Author](#author)

---

## Overview

Most interview prep tools rely on **static question banks** — the same questions, the same answers, no personalisation. This platform fixes that by using **Gemini AI** to generate fresh, role-specific questions every session, evaluate your answers, and give you structured feedback with actionable improvement points.

**20+ active users onboarded in 2 weeks — zero marketing, purely peer referrals.**

---

## Live Demo

🌐 **[Try the Platform](https://your-demo-link.vercel.app)**

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Next.js (SSR), React.js |
| Backend | Node.js, Express.js |
| AI | Google Gemini AI API |
| APIs | REST APIs |
| Rendering | Server-Side Rendering (SSR) |
| Analytics | Custom session tracking |

---

## Key Features

- 🧠 **Dynamic AI Question Generation** — Gemini AI generates role-specific questions tailored to job title and domain (SWE, Data, PM, DevOps, etc.)
- 📝 **Structured Performance Feedback** — scores each answer, flags weak areas, and gives improvement suggestions
- ⚙️ **Rate-Limit Handling** — monitors Gemini API quota per session with graceful fallback to cached question sets
- ⚡ **Next.js SSR** — fast initial page loads and SEO-optimised session history pages
- 📊 **Session Analytics Dashboard** — accuracy trends, topic coverage, and weak-area heatmaps across all sessions
- 🔄 **Multi-role Support** — SWE, Data Engineer, Product Manager, DevOps, and more

---

## How It Works
User selects role + difficulty
│
▼
Node.js backend builds prompt with role context + difficulty tier
│
▼
Gemini AI API generates 5–10 fresh role-specific questions
│
▼
User answers each question in the interactive Q&A flow
│
▼
Gemini evaluates the answer → returns score + feedback
│
▼
Session data saved → Analytics dashboard updated
│
▼
User views accuracy trend, weak areas, and improvement plan
---

## Architecture
┌──────────────────────────────────────────────┐
│              Next.js Frontend                 │
│                                               │
│  ┌─────────────────┐   ┌───────────────────┐  │
│  │  SSR Pages      │   │  React Components │  │
│  │  (session view) │   │  (Q&A flow, dash) │  │
│  └────────┬────────┘   └────────┬──────────┘  │
│           │ REST API calls       │             │
└───────────┼──────────────────────┼─────────────┘
│                      │
▼                      ▼
┌──────────────────────────────────────────────┐
│              Node.js API Server               │
│                                               │
│  ┌─────────────────┐   ┌───────────────────┐  │
│  │  Gemini API     │   │  Rate-Limit       │  │
│  │  Orchestration  │   │  Middleware       │  │
│  └────────┬────────┘   └───────────────────┘  │
│           │                                   │
│  ┌────────▼────────┐   ┌───────────────────┐  │
│  │  Session Store  │   │  Analytics Engine │  │
│  └─────────────────┘   └───────────────────┘  │
└──────────────────────────────────────────────┘
│
▼
Google Gemini AI API
---

## Getting Started

### Prerequisites

- Node.js v18+
- Google Gemini API key ([Get one here](https://makersuite.google.com/app/apikey))

### Installation

```bash
# Clone the repo
git clone https://github.com/siramkrishnapriya-cell/AI-Mock-Interview-Platform.git
cd AI-Mock-Interview-Platform

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env.local

# Run development server
npm run dev
Open http://localhost:3000

Environment Variables
GEMINI_API_KEY=your_gemini_api_key
NEXT_PUBLIC_API_URL=http://localhost:5000
SESSION_SECRET=your_session_secret
GEMINI_RATE_LIMIT_PER_USER=50
GEMINI_FALLBACK_ENABLED=true

API Reference
|Method|Endpoint                 |Description                           |
|------|-------------------------|--------------------------------------|
|POST  |`/api/session/start`     |Start a new interview session         |
|POST  |`/api/questions/generate`|Generate AI questions for role + level|
|POST  |`/api/answers/evaluate`  |Submit answer, get AI feedback + score|
|GET   |`/api/analytics/:userId` |Fetch session history and analytics   |
|GET   |`/api/session/:id`       |Get full session details              |

Project Structure
AI-Mock-Interview-Platform/
├── app/
│   ├── page.tsx
│   ├── session/
│   └── analytics/
├── components/
│   ├── QuestionCard.tsx
│   ├── FeedbackPanel.tsx
│   └── AnalyticsDashboard.tsx
├── server/
│   ├── routes/
│   │   ├── questions.js
│   │   └── analytics.js
│   ├── middleware/
│   │   └── rateLimiter.js
│   └── services/
│       └── geminiService.js
├── .env.example
└── README.md

Author
Siram Krishna Priya
📧 siramkrishnapriya@gmail.com
