# Projects Overview

This repository contains multiple projects under the **Project 7UN** umbrella. Below is a summary of each project.

---

## 🌟 sun-me

**Type:** Personal Portfolio Website
**Status:** Active Development
**Tech Stack:** Next.js 14+, TypeScript, Tailwind CSS, Playwright

### Description
A modern personal portfolio website showcasing professional work, skills, and contact information.

### Key Features
- Server-side rendered with Next.js App Router
- Responsive, mobile-first design
- Sections: Home, About, Projects, Resume, Contact
- Server-side contact form with email delivery (via Resend)
- End-to-end testing with Playwright
- Deployed on Vercel with CI/CD via GitHub Actions

### Quick Start
```bash
cd sun-me
npm install
npm run dev          # Development server at http://localhost:3000
npm test             # Run Playwright tests
```

### Documentation
- [CLAUDE.md](sun-me/CLAUDE.md) - Development guidelines
- [DEPLOYMENT.md](sun-me/DEPLOYMENT.md) - Deployment instructions

---

## 🎨 Taggd.it

**Type:** Graffiti Sharing Community
**Status:** Legacy (2013)
**Tech Stack:** Ruby on Rails 4.0, CarrierWave, Geocoder

### Description
A community platform for sharing street art and graffiti photos with geolocation-based discovery.

### Key Features
- Photo uploads with automatic geolocation extraction
- Location-based tagging for discovery
- Community rating system
- Mobile-friendly interface
- Image hosting with CarrierWave and Fog

### Authors
- Scott Golembiewski
- Robin Swenson-Healey

### License
MIT License (2013)

### Quick Start
```bash
cd Taggd.it
bundle install
rails server
```

---

## 🎭 club-stroll-promo

**Type:** Interactive Theatre Promo
**Status:** Active
**Tech Stack:** Astro, SEO, Marketing

### Description
Promotional website for an in-person interactive play based on Kansas City's rich history of jazz and nightlife. Features immersive storytelling, live performances, and audience participation to bring the vibrant era of the 1920s to life.

### Key Features
- Built with Astro for optimal performance
- SEO-optimized for event promotion
- Marketing-focused design
- Showcases interactive theatre experience

### Links
- GitHub: [rjswenson/club-stroll-promo](https://github.com/rjswenson/club-stroll-promo)

---

## ☀️ sun-online

**Type:** AI-Powered Content Server
**Status:** Active (Featured)
**Tech Stack:** Elixir, Python, FastAPI, AI/ML

### Description
An AI-powered content server using open source archives (Library of Congress, Avalon Project, Fordham University) to deliver educational content with clear transcriptions.

### Key Features
- AI/ML-powered content delivery
- Integration with major educational archives
- FastAPI backend for high performance
- Elixir for scalable concurrent processing

### Links
- Live: [7un.online](https://7un.online)

---

## Repository Management

This repository uses **bd (beads)** for issue tracking and task management. See [AGENTS.md](AGENTS.md) for workflow instructions.

### Common Commands
```bash
bd ready              # Find available work
bd show <id>          # View issue details
bd update <id> --status in_progress
bd close <id>         # Complete work
bd sync               # Sync with git
```

---

## Project Status Summary

| Project | Type | Status | Tech Stack |
|---------|------|--------|------------|
| sun-me | Portfolio | Active | Next.js, TypeScript |
| Taggd.it | Community | Legacy | Rails 4.0 |
| club-stroll-promo | Theatre Promo | Active | Astro |
| sun-online | AI Content Server | Active | Elixir, Python, FastAPI |

---

Last Updated: 2026-01-03
