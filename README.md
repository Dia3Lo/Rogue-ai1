# ROGUE AI — Local-only Creative Prototype

This is an honest, phone-first progressive web app prototype. It makes **no AI generation API calls** and contains no links that launch external image/video services. It can be hosted as static files and cached for offline use after the first visit.

## What works now
- Dark mobile UI and personality preference controls stored in local browser storage.
- Procedural image artwork generated with the Canvas API and export to PNG. This is **not** AI image generation.
- Procedural motion preview, plus a best-effort browser recording/export attempt when iOS Safari exposes `captureStream` and `MediaRecorder`. This is **not** AI text-to-video or image-to-video. Export compatibility on iOS is not guaranteed.
- Offline app shell via service worker after it has been served over HTTPS and cached.

## What is NOT implemented
- No real local language model is bundled, so AI chat is intentionally disabled.
- No diffusion image model is bundled; generated images are procedural graphics, not model-generated images.
- No AI video model is bundled; motion is procedurally drawn.
- No app-store/native iOS package is provided.

A true local AI build needs model weights plus an inference runtime compatible with iOS. Browser PWA support alone does not provide a built-in general-purpose LLM, diffusion model, or video model. A fully local video model may exceed practical iPhone memory/thermal limits. These models and runtimes are not included here, and this prototype does not pretend otherwise.

## Deploy using only your iPhone
1. Download and extract the ZIP in the Files app.
2. In Safari, sign into GitHub and create a repository. Upload the contents of this folder to the repository root, then commit. Do not add secrets or API keys.
3. In the repository settings, enable GitHub Pages for the `main` branch and root directory. Wait for the HTTPS site to publish.
4. Open the published site in Safari, visit all tabs once, then Share → Add to Home Screen. The service worker caches the shell for later offline use.
5. Test in Airplane Mode. The Canvas artwork should still generate. The video recorder may not be available in every iOS Safari session.

## Privacy and networking
The app source has no remote AI API calls, external runtime imports, or redirects. GitHub Pages is only the static file host. Initial website load requires internet; offline availability begins after service-worker caching. User settings are stored in `localStorage`; generated art is drawn in the browser. A selected image for the motion preview is read locally and is not uploaded.
