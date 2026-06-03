# Project Case Studies

This page is a quick, recruiter-friendly overview of selected projects. Each entry links to a deeper case study in `/projects`.

> Format used: **Google XYZ** — *Accomplished X as measured by Y by doing Z.*

---

## 1) Florida Guest House — Booking Platform (Production)
**Stack:** Bun · Hono · SQLite · Tailwind (CDN) · Server-side HTML

- **Accomplished a mobile-first booking flow** as measured by **successful bookings on low-end devices** by **using server-rendered pages + minimal JS and a lightweight runtime (Bun).**
- **Accomplished predictable booking state transitions** as measured by **fewer “stuck” bookings** by **auto-expiring pending bookings after 15 minutes and enforcing lifecycle rules.**
- **Accomplished faster read performance** as measured by **lower DB contention under browsing** by **enabling SQLite WAL mode and using prepared statements.**

**Case study:** see `projects/florida-guest-house.md`

---

## 2) Student Clearance / Clearance Management System (Production)
**Stack:** Node.js · RBAC · Audit Logging · Relational DB

- **Accomplished end-to-end clearance visibility** as measured by **clear per-department progress** by **building dashboards and a role-based workflow.**
- **Accomplished traceability for approvals** as measured by **auditable state changes** by **logging every approval/rejection with timestamps and actor identity.**

**Case study:** see `projects/student-clearance-system.md`

---

## 3) Mobile Money Workaround — SMS-based Merchant Payments
**Stack:** Workflow automation (LlamaLab Automate) · Event parsing · VPS / on-site deployment

- **Accomplished payment tracking without official APIs** as measured by **structured payment events** by **parsing merchant-payment SMS messages into normalized records.**
- **Accomplished reusable automation workflows** as measured by **multiple business use-cases (voucher sales, notifications, reconciliation)** by **routing events through Automate flows and a lightweight server dashboard.**

**Case study:** see `projects/momo-airtel-sms-payments.md`

---

## 4) ClipLogger — Clipboard Monitoring Tool (Windows)
**Stack:** Python · pywin32 · watchdog · psutil · wmi

- **Accomplished detailed clipboard/file-operation logs** as measured by **timestamped events with storage-type detection** by **combining clipboard monitoring + filesystem watchers + system inspection.**

**Case study:** see `projects/cliplogger.md`

---

## 5) FoundUG — Lost & Found Web App (Archived)
**Stack:** Next.js · Tailwind · Zod · Supabase

- **Accomplished fast listing workflows** as measured by **validated, consistent submissions** by **using Zod + Supabase and a modern Next.js UI.**

**Case study:** see `projects/foundug.md`
