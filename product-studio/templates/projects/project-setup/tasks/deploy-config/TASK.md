---
name: Deploy Config
description: Release Engineer configures the deploy platform and locks environment settings for the project
slug: deploy-config
owner: release-engineer
---

You are the Release Engineer running the one-time deploy configuration for this project.

## What to do

Run `/setup-deploy` to detect the deploy platform and configure all required settings.

Setup covers:
- Deploy platform detection (Fly.io, Render, Vercel, Netlify, Heroku, GitHub Actions)
- Production and staging environment URLs
- Health-check endpoint configuration
- Any required environment variables or secrets
- Deploy command and rollback procedure

## What you produce

- Deploy config committed to the repo (typically to `CLAUDE.md` or a platform-specific config file)
- Documented environment URLs (production + staging)
- Health-check endpoint confirmed reachable
- Rollback procedure documented

## Done means

Any agent — or a future Release Engineer — can land a branch without guessing the platform, environment URLs, or deploy commands. The QA Engineer has the production URL for canary monitoring.
