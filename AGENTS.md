# PsalmistRuth GospelHub — Base44 dev environment

## What this repo is
A **Blogger template** (XML using Blogger's `b:` namespace tags: `<b:widget>`, `<data:blog.*>`, `<b:loop>`, etc.). The two source files — `Psalmist api blog` and `PsalmistRuth_GospelHub.xml` — are identical. This template only renders when uploaded to Blogger.com; it cannot run as-is in a browser.

## How it runs here
Since the Blogger template tags need Blogger's server-side rendering, the preview serves a **static HTML rendering** of the template at `index.html` (repo root), built from the template's own CSS and the embedded sidebar widgets (which are already plain HTML/JS in CDATA). The sidebar's interactive widgets — AI Song Studio (Create/Explore tabs), Submit Your Music form, Gospel Streams embeds — are preserved verbatim and work in the browser.

## Stack
- Static site served by `nginx:alpine` via `docker-compose.base44.yml`.
- No backend, no database, no build step, no external secrets required.
- The AI/music API endpoints in the widget JS (`/api/middleware/suno`, `/api/middleware/gemini`) are commented out and return mock responses — they would need a Cloudflare Worker or similar middleware to function for real.

## Verify it works
```
docker compose -f docker-compose.base44.yml up -d
curl -sf -H "Host: external-preview.example.com" http://localhost:3000/   # should return the HTML
```
Preview is on host port 3000.

## Editing
- `index.html` is the rendered preview — edit it to change what shows in the preview.
- The original Blogger template files (`Psalmist api blog`, `PsalmistRuth_GospelHub.xml`) are the source of truth for the actual Blogger theme; changes there are not reflected in the preview unless re-rendered into `index.html`.
