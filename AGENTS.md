# PsalmistRuth GospelHub — Base44 Dev Notes

## What this project is
A **Blogger theme template** (XML) for a gospel music blog called "PsalmistRuth GospelHub".
The repo contains two identical Blogger theme XML files (`PsalmistRuth_GospelHub.xml` and `Psalmist api blog`).
These are not runnable web apps — they are templates meant to be uploaded to Blogger.com.

## How it runs in Base44
Since Blogger templates can't be served directly, `index.html` is a **static HTML rendering** of the
template — extracted CSS, sample blog posts, and all sidebar widgets (AI Song Studio, Submit Music,
Gospel Streams, Sections) with their original JavaScript intact.

Served by `nginx:alpine` via `docker-compose.base44.yml` on port 3000.

## No secrets required
The template's API endpoints (`/api/middleware/suno`, `/api/middleware/gemini`) are mocked in
JavaScript. No external credentials are needed to run the preview.

## Verification
- `curl -sf http://localhost:3000/` returns the rendered page
- `curl -sf -H "Host: external-preview.example.com" http://localhost:3000/` also works (nginx accepts any host)
