# Changelog

What changed in each Apinx version. Apinx Cloud always runs the latest one.

## 1.3.1 (2026-11-06)

- Apinx Cloud: a database migration that 1.3.0 could not apply on PostgreSQL now applies.
  Nothing changes on premises.

## 1.3.0 (2026-11-06)

- **Request validation:** the new `validate` policy checks bodies, query parameters, headers
  and path parameters against JSON Schema. An OpenAPI import keeps its schemas and binds them
  for you; a request that does not match is refused with every violation named.
- **OpenTelemetry:** one span per request to your collector over OTLP (gRPC or HTTP), every
  policy step and backend attempt on it, the caller's `traceparent` continued and passed on to
  your backends, and the trace ID on each access log line. In Apinx Cloud each organization
  sends its traces to its own collector.
- **Logs to your tools:** the access log goes straight to Grafana Loki, Elasticsearch or
  OpenSearch, Seq, a syslog server, or any TCP collector (Vector, Fluent Bit, Logstash), on a
  queue that never delays a request. A Grafana dashboard for the Loki log ships with
  on-premises releases.
- **Weighted canary:** send a share of a route's traffic to a second upstream, with a header
  your testers use to pin either side and a fallback to the stable side.
- **Compression:** the `compress` policy answers with gzip or Brotli when the caller accepts
  it.
- **Analytics:** period chips (last hour to last 30 days, or your own), key figures against
  the previous period, a traffic chart you zoom by dragging, and a sortable operations table.
- The request inspector can be shared across instances through Redis, so a cluster shows one
  list of traces.
- **Security:** sign-in is throttled per client address across accounts; JWT key sets reject
  RSA keys under 2048 bits, cap the keys they accept and the clock skew they allow; OIDC
  sign-in fails closed without an asymmetric algorithm; HSTS on a secure console; TLS by
  default to a PostgreSQL server on another host; a connection cap on every listener; query
  parameters that carry credentials are masked in traces. In Apinx Cloud, WebSocket backends
  pass the same address checks as every other connection, and secret references are refused.
- **Performance and memory:** a lighter request path, one Redis round trip per Cloud request
  for its plan, analytics merged in the database, a separate queue per telemetry sink, a
  faster SOAP decoder and leaner service callouts. In Apinx Cloud, idle organizations release
  their connections.
- Apinx Cloud: Enterprise bursts up to 2,000 calls a second, and an introductory price for
  the first year ([pricing](https://apinx.io/pricing)).
- New guides: [Grafana and other tools](https://apinx.io/docs/guides/integrations/) and
  [Authentication at a glance](https://apinx.io/docs/concepts/authentication/).

## 1.2.2 (2026-10-30)

- API health lists only the APIs in trouble, and the health grid fits the page.
- Search an API's operations by name or path on its Develop tab.

## 1.2.1 (2026-10-30)

- Analytics keep the exact status of every error, with one filter bar and one Errors section
  by status.

## 1.2.0 (2026-10-29)

- **Access tokens issued by Apinx:** applications get client IDs and secrets beside their API
  keys and trade them for access tokens (OAuth 2 client credentials), with refresh tokens that
  rotate on every use, reuse detection, sessions you list and revoke, and a signing key per
  environment rotated with an overlap. The `oauth2` policy accepts them.
- Authentication policies bound together are alternatives: a request needs one credential
  that one of them accepts.
- A Postman collection that uses client credentials against the gateway is imported with the
  `oauth2` policy.
- Dashboards show errors by status code, with 5xx in red. A version without a label can be
  given one.

## 1.1.13 (2026-10-28)

- Speed has its own colours in analytics: slow is orange, red is kept for errors.

## 1.1.12 (2026-10-27)

- API health per operation: the worst operations first, and each error with its operation.

## 1.1.11 (2026-10-27)

- **What is wrong with my APIs:** the Analytics page ranks APIs by trouble, with a health grid
  over time, performance by speed band (1, 2 and 4 seconds) and errors with since when.
- The APIs page shows a card per API.

## 1.1.10 (2026-10-27)

- Apinx Cloud: a cache purge clears the environment's own cache, and an organization's
  environments share one cache budget.

## 1.1.9 (2026-10-27)

- **SOAP backends as JSON APIs:** the `soap` policy builds the envelope from the caller's
  JSON, decodes the answer to JSON and turns a fault into a coded error. Import a WSDL and the
  API, its operations and their templates are proposed for you to review.
- A release that compiles a draft differently can still be deployed.

## 1.1.8 (2026-10-27)

- **Products offer chosen operations** of an API, and tags beside each API and operation say
  who can call it.
- A rate limit bound on an API counts its operations together; bound on one operation, that
  operation alone.
- A changed listener takes over the open socket, so no connection is refused.
- Lower cost per request, and fixes from an architecture review.

## 1.1.7 (2026-10-26)

- Operations can be switched off, and the Operations tab lists the paths each catch-all
  served.

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
