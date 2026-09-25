# Synthesis Lab

A browser-based creative studio for [MUAPI.ai](https://muapi.ai) — browse 300+ AI models and generate images, videos, audio, and more from a single interface.

![Dark theme](https://img.shields.io/badge/theme-dark%20%2F%20light-1a2744)
![No build](https://img.shields.io/badge/build-none%20required-00d4aa)
![Responsive](https://img.shields.io/badge/responsive-mobile%20%2F%20tablet%20%2F%20desktop-8b5cf6)

## Features

**Model Explorer** — Search and browse models across 8 categories: text-to-image, image-to-image, text-to-video, image-to-video, audio, sound effects, enhance, and edit.

**Studio** — Stacked, collapsible generation cards organized by type. Select a model from the explorer and it opens the right card with that model pre-selected.

- **Image**: Text-to-image (FLUX, Midjourney, Stable Diffusion, GPT-4o, Seedream, etc.) and image editing (Kontext, Reve, etc.)
- **Video**: Text-to-video (Veo3, Kling, Runway, Sora, etc.) and image-to-video animation
- **Audio**: Music generation (Suno) and sound effects (MMAudio)
- **Enhance**: Upscale, background removal, face swap, Ghibli stylization
- **Edit**: Video clipping and lip sync

**Gallery** — Locally persisted collection of your generations with type filtering and detail view.

**Sharing** — Native share sheet on mobile, clipboard copy everywhere else. Formatted with model name, prompt, and media URL.

**Security** — API key stored in browser localStorage, masked in UI, transmitted only to your configured MUAPI endpoint.

## Getting Started

1. Open `index.html` in any browser
2. Enter your MUAPI.ai API key when prompted
3. Start generating

No build step. No server. No dependencies beyond Google Fonts loaded at runtime.

## Hosting

Drop `index.html` on any static host:

- **GitHub Pages**: Push to a repo, enable Pages in Settings → Pages → Deploy from branch
- **Netlify / Vercel**: Drag and drop the file
- **Any web server**: Serve the single file

Each visitor enters their own API key — nothing is stored server-side.

## API Notes

The app uses MUAPI.ai's async generation pattern:

1. Submit a generation request → receive a `request_id`
2. Poll `/v1/predict/{id}` until the job completes
3. Display the result (image/video/audio URL)

When running inside sandboxed environments (like Claude artifacts), direct API calls may be blocked by CORS. The app detects this and shows a copiable `curl` command as fallback.

## Responsive Design

- **< 360px**: Single column, stacked controls, condensed header
- **< 480px**: Vertical form field stacking
- **768px+**: 2-column gallery, larger gutters
- **900px+**: 2-column studio cards
- **1200px+**: Sidebar navigation, 3-column model grid
- **1400px+**: 4-column models, 5-column gallery

All touch targets meet the 44px minimum. Form inputs use 1rem font to prevent iOS auto-zoom.

## Tech

Single HTML file, vanilla JS, no framework. ~1200 lines total.

- **Fonts**: Outfit (display), DM Sans (body) via Google Fonts
- **Theme**: Dark-first with full light mode support and system preference detection
- **Storage**: localStorage for API key, gallery, and theme preference

## License

MIT
