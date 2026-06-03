# Florida Guest House — Booking Platform (Production)

## Summary (XYZ)
- **Accomplished a mobile-first booking flow** as measured by **successful bookings on low-end devices** by **using server-rendered pages + minimal JS with Bun + Hono.**
- **Accomplished predictable booking state transitions** as measured by **fewer “stuck” bookings** by **auto-expiring pending bookings after 15 minutes and enforcing lifecycle rules.**
- **Accomplished better read performance** as measured by **more responsive browsing** by **enabling SQLite WAL mode and using prepared statements.**

## What it does
- Room listings + add-on services
- Booking creation and management
- Payment handled manually via MTN MoMo / Airtel Money merchant numbers + OTP confirmation step

## Architecture (high level)
- Hono server renders HTML
- SQLite stores rooms/bookings
- Static images served from `public/images/rooms/`

## Reliability / engineering notes
- WAL mode enabled on SQLite
- Pending bookings expire after 15 minutes (enforced on checkout revisit)

## Screenshots
Add screenshots under:
- `assets/screenshots/florida-guest-house/`

Then link them here.
