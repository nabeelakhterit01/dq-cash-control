# DQ Cash Control — Hostinger Node.js edition

Standalone Express + MySQL application for a small retail outlet. No PAR Brink integration.

## Hostinger setup
1. Create a MySQL database in Hostinger hPanel and save host, database, username, password privately.
2. In Hostinger Web Apps, import this GitHub repository, branch `main`, and choose Node.js. Build: `npm install`; Start: `npm start`.
3. Set environment variables from `.env.example` using Hostinger's environment settings, **not GitHub**. Set a unique 32+ byte `SESSION_SECRET` and a strong `BOOTSTRAP_MANAGER_PASSWORD` on first launch.
4. Visit the temporary HTTPS domain. Sign in as `manager` with bootstrap password. Change manager password via Accounts and set staff passwords before use.
5. Manager can set approved store public IP(s) via Store Network. Blank means staff network restriction disabled.
6. Configure a persistent MySQL database backup policy and verify that file uploads persist between deployments. **Hostinger Web Apps file storage persistence is not verified**: do not rely on report attachments for production until tested or migrated to durable object storage.

## Features
Manager/staff accounts; daily cash count and reconciliation; denomination entry; PAR cash total entered manually; optional PAR report attachment; history; audit log; CSV export; manager-only IP allowlist and password management.

## Calculation
Expected cash = opening float + PAR cash + other cash in − expenses − cash drops.
Variance = counted physical cash − expected cash.
Confirm store accounting conventions before using with real financial data.

## Security and launch checklist
This is a deployment candidate, **not independently audited for production financial use**. Change bootstrap passwords immediately; enable HTTPS; verify sessions, proxy configuration, backups, database persistence, upload persistence, IP filtering, rate limiting, and data access before live use. An IP allowlist cannot prove physical presence when a store VPN is used. Do not publish credentials, actual reports, or financial data to GitHub. Repo should be private.
