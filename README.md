### Hi there 👋, I'm Denny

**Full-Stack Developer · IT Infrastructure Engineer · AI Automation Builder**

**React & Next.js | NestJS & Express | Docker & Kubernetes | PostgreSQL & MongoDB | AI Integration | CI/CD Pipelines | Linux SysAdmin | Microservices Architecture | API Design | Data Engineering**

I build full-stack web apps, design scalable infrastructure, and automate workflows with AI. From frontend interfaces to backend systems, database optimization to production deployment — I handle the whole pipeline end-to-end.

---

## Tech Stack

### ⌨️ Languages & Scripting
![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?style=flat-square&logo=javascript) ![TypeScript](https://img.shields.io/badge/-TypeScript-3178C6?style=flat-square&logo=typescript) ![Python](https://img.shields.io/badge/-Python-3776AB?style=flat-square&logo=python) ![PHP](https://img.shields.io/badge/-PHP-777BB4?style=flat-square&logo=php) ![SQL](https://img.shields.io/badge/-SQL-4479A1?style=flat-square&logo=mysql) ![Bash](https://img.shields.io/badge/-Bash-4EAA25?style=flat-square&logo=shell)

### 🎨 Frontend
![React](https://img.shields.io/badge/-React-61DAFB?style=flat-square&logo=react) ![Next.js](https://img.shields.io/badge/-Next.js-000000?style=flat-square&logo=nextdotjs) ![Vue.js](https://img.shields.io/badge/-Vue.js-4FC08D?style=flat-square&logo=vuedotjs) ![Svelte](https://img.shields.io/badge/-Svelte-FF3E00?style=flat-square&logo=svelte) ![Astro](https://img.shields.io/badge/-Astro-BC52EE?style=flat-square&logo=astro) ![Tailwind CSS](https://img.shields.io/badge/-TailwindCSS-06B6D4?style=flat-square&logo=tailwindcss)

### 🖥️ Backend
![NestJS](https://img.shields.io/badge/-NestJS-E0234E?style=flat-square&logo=nestjs) ![FastAPI](https://img.shields.io/badge/-FastAPI-009688?style=flat-square&logo=fastapi) ![Node.js](https://img.shields.io/badge/-Node.js-339933?style=flat-square&logo=nodedotjs) ![Express](https://img.shields.io/badge/-Express-000000?style=flat-square&logo=express) ![Prisma](https://img.shields.io/badge/-Prisma-2D3748?style=flat-square&logo=prisma)

### 💾 Database & Storage
![MySQL](https://img.shields.io/badge/-MySQL-4479A1?style=flat-square&logo=mysql) ![Redis](https://img.shields.io/badge/-Redis-DC382D?style=flat-square&logo=redis) ![AWS S3](https://img.shields.io/badge/-AWSS3-569A31?style=flat-square&logo=amazonaws)

### ☁️ DevOps & Tools
![Docker](https://img.shields.io/badge/-Docker-2496ED?style=flat-square&logo=docker) ![Linux](https://img.shields.io/badge/-Linux-333?style=flat-square&logo=linux) ![Nginx](https://img.shields.io/badge/-Nginx-009639?style=flat-square&logo=nginx) ![Git](https://img.shields.io/badge/-Git-F05032?style=flat-square&logo=git) ![Cloudflare](https://img.shields.io/badge/-Cloudflare-F38020?style=flat-square&logo=cloudflare) ![Vite](https://img.shields.io/badge/-Vite-646CFF?style=flat-square&logo=vite) ![VS Code](https://img.shields.io/badge/-VSCode-007ACC?style=flat-square&logo=visualstudiocode)

---

## Featured Projects

### ⭐ Job Scout AU/NZ — Production AI-Assisted Job Discovery & Screening Pipeline

**v1.0.0 · private repo · LIVE** — [@Aus_nz_jobs_notify_bot](https://t.me/Aus_nz_jobs_notify_bot), runs automatically 2× daily on a production VPS as a least-privilege service.

Not a scraper — an end-to-end **ETL + AI screening pipeline** that turns raw job listings from multiple ATS platforms into a handful of qualified, evidence-scored opportunities delivered to Telegram:

```text
ATS APIs (Greenhouse/Lever/Ashby) → Normalizer (ETL) → Fingerprint dedup →
Rule engine (deterministic, no AI) → Top-5 role prefilter → DeepSeek multi-role
screening → Deterministic scoring → Notification gate → Telegram (dedup-safe)
```

**Engineering actually practiced:**

- **Python ETL pipeline** — normalizes 3 different ATS API formats (Greenhouse/Lever/Ashby, official APIs, no ToS-violating scraping) into one internal schema; SHA-256 fingerprinting for idempotent dedup (120 jobs run 1 → 0 new on run 2)
- **Deterministic rule engine** — weighted keyword scoring in JSON config, filters 120 jobs → 14 without spending a single AI token; 20 career role profiles are config-driven (add a role = edit JSON, no code change)
- **LLM integration done right** — DeepSeek V4 Flash, JSON mode, `temperature=0`, evidence-based assessment (visa status must cite evidence: CONFIRMED/POSSIBLE/UNKNOWN/NO, never invented); AI is the *judge*, Python computes the final score (35% technical / 25% career / 20% location / 20% visa)
- **Token & cost optimization** — top-5 role prefilter solved prompt truncation (was 5/14 failing at 4096 tokens → 14/14 clean at 2048); AI result cache by description hash → reruns cost **0 API calls, 0 tokens**
- **Policy layer** — Notification Gate V1 separates scoring from decision (APPLY ≥75, MAYBE ≥60); once sent, `notified=1` so nothing is ever delivered twice
- **Production hardening** — cron + flock anti-overlap, per-stage timeouts, exponential backoff retry (no job ever lost), bounded logs, dedicated non-root user, no ports opened, isolated directory, secrets in 600-perm env file
- **Testing** — 167 unit + integration + regression tests (all mocked)

**Stack:** `Python` `SQLite` `DeepSeek` `ATS APIs` `Telegram Bot API` `cron` `Linux`

---

| Project | What it does | Stack |
|---------|-------------|-------|
| **[LMS Platform](https://github.com/adityadenny/readme)** *(internal)* | Production learning management system with auth/RBAC, H5P interactive content, video streaming, certificate generation, Google Drive backup | `NestJS` `React 19` `Prisma` `MySQL` `Redis/BullMQ` `Docker` `Tailwind CSS v4` |
| **[VidKupas](https://github.com/adityadenny/vidkupas)** | Offline video/audio transcription and AI summarizer with progress tracking and auto-generated subtitles | `Python` `FastAPI` `OpenAI Whisper` |
| **[Earthquake Bot](https://github.com/adityadenny/latest-indonesia-earthquake)** | Real-time earthquake alert bot using official BMKG data. Runs free on edge cloud. Try it: [@awas_gempa_bot](https://t.me/awas_gempa_bot) ⭐1 | `TypeScript` `Cloudflare Workers` `Telegram Bot API` |
| **[LinkLeads](https://github.com/adityadenny/linkleads)** | Concurrent web scraper that extracts emails, phone numbers, and social links from websites | `Python` `BeautifulSoup` `ThreadPoolExecutor` |
| **[Satu Lagi Boss](https://github.com/adityadenny/satu-lagi-boss)** | Modern frontend app built with SvelteKit | `Svelte` `SvelteKit` `Vite` |
| **[Tenang Ada Gue](https://github.com/adityadenny/tenang-ada-gue)** | Campaign site migrated from WordPress to Jamstack/Astro. Zero-server deployment on edge. | `Astro` `Three.js` `GSAP` `Cloudflare Workers` |
| **[Cashier POS](https://github.com/adityadenny/cashier)** | Point-of-sale app for retail transaction management | `Vue` `Nuxt` `Vuetify` |
| **[Brightlings Academy](https://github.com/adityadenny/brightlings-academy-kids-edu)** | Premium preschool landing page with Scandinavian design | `HTML5` `Tailwind CSS` |

---

## Experience

**IT Generalist / Staff Engineer** *(nonprofit organization)*

Managed the full stack of infrastructure and applications across 3 production VPS servers:

- Server ops for multiple Ubuntu distributions, Nginx reverse proxy, Docker containers, MySQL, Redis
- Built tiered backup systems with rclone + Google Shared Drive (30/180 day retention), Telegram notifications on success or failure
- Handled repeated production incidents including chronic disk full issues through data-driven root cause analysis and mass in-place compression without breaking database references
- Full development lifecycle for production apps including LMS, automation bots, and campaign sites
- Deployed production automation as least-privilege Linux services: cron scheduling, flock concurrency control, retry/backoff, idempotent pipelines, AI API integration with caching and deterministic post-processing
- Firewall management, TLS hardening, vulnerability audits, network reconnaissance
- Wrote standardized runbooks, postmortems, and operational documentation

---

<div align="center">

Thanks for stopping by! If you find my projects useful, feel free to fork them or open an issue. 🙏

</div>

<br>
</sub>Hakuna Matata 🦁</sub>
