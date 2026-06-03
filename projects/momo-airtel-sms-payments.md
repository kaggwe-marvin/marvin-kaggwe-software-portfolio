# Mobile Money Workaround — SMS-based Merchant Payments

## Summary (XYZ)
- **Accomplished payment tracking without official APIs** as measured by **structured payment events** by **parsing merchant-payment SMS messages into normalized records.**
- **Accomplished reusable automation workflows** as measured by **multiple supported business flows (voucher sales, notifications, reconciliation)** by **routing events through LlamaLab Automate and a lightweight dashboard.**

## Problem
In some environments, official APIs are limited/unavailable, but businesses still need reliable payment visibility.

## Approach
- Read merchant SMS notifications
- Parse into structured events (amount, sender, reference, timestamp, status)
- Trigger automations: notify, log, reconcile, export

## Outputs
- Dashboard-friendly event stream
- Reporting + reconciliation support

## Notes
If you later integrate an official API, this SMS pipeline can remain as a fallback/verification channel.

## Screenshots / diagrams
- `assets/diagrams/momo-airtel-sms-payments/`
- `assets/screenshots/momo-airtel-sms-payments/`
