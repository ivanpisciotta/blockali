# Blockali

A blockchain learning platform. Students follow learning paths, read lessons and take quizzes; admins create and manage the content.

Final team project for the 4Geeks Academy Full Stack Developer program (2026).

## Stack

React (Vite) · Flask · SQLAlchemy · PostgreSQL · JWT

## Features

- Sign up and login with JWT and hashed passwords
- Two roles (admin / student), checked on both the frontend and the backend
- Learning paths → modules → lessons in Markdown
- Quizzes with automatic grading (70% to pass) and retry
- Admin panel to create learning paths, modules and lessons
- Live crypto price ticker (CoinGecko API, 60-second refresh)
- If the backend is down, the quiz view shows sample content instead of breaking
- Seed script that can run any number of times without creating duplicates

## My contributions

- **Security:** replaced plain-text passwords with werkzeug hashing, with its migration; initialized `JWTManager`, which fixed the 500 errors on every protected endpoint
- **Admin panel:** `/admin` page with role-based access and forms for paths, modules and lessons
- **Quiz view:** answer selection, grading, retry and the sample-content fallback
- **Landing page:** "How it works", "Who it's for" and call-to-action sections, footer, SVG logo and the live crypto ticker
- **Content:** quiz questions in the seed data (4 per lesson, each with an explanation)
- **Fixes to the shared code:** a missing reducer action that left the learning paths section empty, a broken import that crashed the frontend, and npm dependencies that were used but never declared

## Design decisions

- **Quiz questions in a JSON column** instead of separate tables: a 3-question quiz and a 10-question quiz use the same structure, with no extra tables or migrations.
- **All API calls go through a services layer.** We started with mock data, and switching to the real backend needed no changes to the UI components.
- **Components split by section**, so the team could work in parallel without merge conflicts.

## Run locally

Requirements: Python 3, Pipenv, Node.js, PostgreSQL.

```bash
# Backend
pipenv install
cp .env.example .env      # set your DATABASE_URL
pipenv run upgrade
pipenv run start

# Frontend (in another terminal)
npm install
npm run start
```

## Team

- Iván Pisciotta — [@ivanpisciotta](https://github.com/ivanpisciotta)
- [@LuisSebastianD](https://github.com/LuisSebastianD)
- [@mieresantonio](https://github.com/mieresantonio)
