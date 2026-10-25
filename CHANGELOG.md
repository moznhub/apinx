# Changelog

What changed in each Apinx version. Apinx Cloud always runs the latest one.

## 1.1.6 (2026-10-25)

- The assistant's **Insert into editor** takes only a whole definition of the same kind. Part
  of one is offered as **Copy** instead.
- The recommended global defaults start the size limit at 1 MB, so they save as suggested.

## 1.1.5 (2026-10-24)

- The assistant can use Claude Sonnet or Claude Haiku, chosen per task.

## 1.1.4 (2026-10-24)

- New policies: `forward` (an allow-list of what reaches the backend) and `mock-response`
  (answer without a backend).
- Composed service callouts, and route **mirroring** to send a copy of traffic to a second
  backend.
- Rate-limit and quota counters survive a publish.
- **File mode** (`apinx gateway run`) reads `${NAME}` and `${NAME:-default}` from the
  environment.
- A configuration audit of who changed what.
- A lower cost per request, and 256 idle connections kept per backend target.

## 1.1.3 (2026-10-23)

- On and off settings in the console are switches.

## 1.1.2 (2026-10-23)

- Fixes to saving plans in the console.

## 1.1.1 (2026-10-23)

- Internal errors are logged with their request ID.
- Sign-in fix for accounts with no organization (Cloud).

## 1.1.0 (2026-10-23)

- **The console assistant:** answers about Apinx, drafts YAML and jq you apply, walk-throughs,
  field help and history. On premises it uses your own Claude API key; it never sees your
  traffic or your secrets.
- **Postman collection import** (v2.0 and v2.1): each request becomes an operation, the
  collection's auth a suggested policy. Keys, tokens and passwords are never imported.

## 1.0.13 (2026-10-22)

- The Needs attention card refreshes itself and gives the last error to the minute.
- Cloud: API keys are loaded after a restart.

## 1.0.12 (2026-10-22)

- **Security:** API keys are scoped to their organization and environment.
- The Needs attention card covers the last 24 hours in plain sentences.
- Faster analytics writes and lighter Overview polling. Components moved to **Admin › About**.

## 1.0.11 (2026-10-21)

- The new Apinx brand across the console and documentation.

## 1.0.10 (2026-10-21)

- Plan rules are checked when an upstream is saved.
- Backend health in the request inspector and the console, with the reason a target is out.

## 1.0.9 (2026-10-21)

- The `jwt` policy discovers its keys from the issuer (OpenID Connect discovery).

## 1.0.8 (2026-10-20)

- **Service callouts:** call other backends before or after the main one, in parallel, and
  stitch their answers into one body.
- Go 1.27.2 security update.
- A failed step in the console leaves nothing half-saved. A dark-mode YAML editor.

## 1.0.4 to 1.0.7 (2026-10-10)

- **Environments:** separate addresses with their own APIs, selected with the
  `X-Apinx-Environment` header.

## 1.0.3 (2026-10-10)

- Applications compared side by side in analytics.
- The WebSocket connection cap applies across instances. The node name is on every log line.

## 1.0.2 (2026-10-10)

- **gRPC pass-through**, unary and streaming, with `grpc://` targets, the gRPC health probe
  and the gRPC status in traces and analytics.
- WebSocket on by default for new routes.

## 1.0.1 (2026-10-09)

- Distributed tracing, multi-factor sign-in for the console, documentation and screenshot
  updates.

## 1.0.0 (2026-10-09)

- First release: the gateway, Admin API and console in one binary, with SQLite or PostgreSQL,
  clustering, products and plans, revisions and rollback, the request inspector and analytics.
