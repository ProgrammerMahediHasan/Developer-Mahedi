# Personal Portfolio (Vue 3 + Vite)

## Local Development
- Install deps: `npm install`
- Run dev: `npm run dev` → http://localhost:5173/

## Contact Form Delivery
Two delivery paths are integrated:
- EmailJS (recommended, no verification): requires 3 env vars
- FormSubmit (fallback): works without keys; first time requires inbox verification

### Configure EmailJS
1) Copy `.env.example` to `.env.local`
2) Set:
```
VITE_EMAILJS_SERVICE_ID=...
VITE_EMAILJS_TEMPLATE_ID=...
VITE_EMAILJS_PUBLIC_KEY=...
```
3) Restart dev server if running.

The contact form reads these variables and sends directly via EmailJS if present; otherwise it posts to FormSubmit and shows success on return.
