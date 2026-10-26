# Hi, I'm Sahil 👋

**Infrastructure & DevOps Engineer** based in Riyadh. I work across the infrastructure and services behind production platforms: deploying, validating, and keeping them observable.

I didn't start in software. I hold a **Mechanical Engineering** degree and began in CAD design (AutoCAD, SolidWorks, ANSYS), then moved into IT and GIS work on major national projects before finding my home in DevOps. That path taught me systems thinking and precision under real-world constraints, and it shapes how I approach infrastructure today: understand the whole system first, then make it robust.

---

## 🛠️ What I work with

**Orchestration & Containers:** Kubernetes (k3s), Docker \
**API & Backend:** Kong API Gateway, Node.js / Koa.js, Python, Java, PostgreSQL, Elasticsearch \
**Observability:** Prometheus, Grafana \
**Cloud & Data:** Oracle Cloud Infrastructure (OCI), Cloudera Data Platform (CDP) \
**Security & Auth:** Kerberos (keytab-based service auth), TLS \
**Foundations:** Linux, Git, networking, Bash

---

## 💼 What I do

At **WeDo Solutions**, I'm part of the team behind the infrastructure for large public-sector platforms, primarily for the **Ministry of Municipal and Rural Affairs and Housing (MOMAH)**. My day-to-day spans working with Kubernetes and Kong, standing up and validating backend services before release, and maintaining Prometheus/Grafana monitoring that helps us catch problems before users do.

---

## 🏗️ Systems I've Worked On

*Production services for public-sector platforms at WeDo Solutions. Code is private (client work). Some are designed by my tech lead and some are mine end to end; my specific role on each is listed below.*

### 📊 NCIM Analytics Dashboard Platform
> A self-hosted Apache Superset platform on Kubernetes serving business and data-platform dashboards over a Kerberos-secured Impala warehouse — 6 live dashboards and 43 datasets, plus an MCP endpoint that lets Claude build new charts and dashboards by prompt.

**Built and maintained by me:**
- Built the container image and Kubernetes deployment on the Apache Superset Operator; an idempotent init step creates the admin, a read-only viewer role and a dedicated MCP service user on every deploy
- Built pipeline-operations and platform-health dashboards: load status and a 24-hour run timeline per layer, data-quality rejections across 100+ tables, table freshness against each table's usual load interval, and Iceberg storage health read from metadata tables at about 1/50 the cost of scanning files
- Added Superset's MCP server so Claude can list data, run read-only SQL and draft dashboards — signed, expiring per-person tokens, a non-admin service identity, SELECT-only SQL, and everything saved as a draft until an admin publishes it
- Moved every chart to live Impala queries with tiered Redis caching (1 h for operations, 24 h for business views), retiring a separate snapshot database so there is one source of truth
- Kerberos from a mounted keytab with no `kinit`, no sidecar and no cron, plus a TLS fix that keeps full CA-chain verification while skipping the hostname check only when connecting by IP
- Hardened the internet-facing deployment: no anonymous access or self-registration, login rate limiting, CSRF and security headers, read-only connections, and embedding and file uploads disabled

`Apache Superset` `Kubernetes` `Helm` `Docker` `Python` `Redis` `Kerberos` `Cloudera Impala` `Apache Iceberg` `MCP`

### 🔌 Read-Only MCP Server for a Kerberos-Secured Warehouse
> An MCP server that lets LLM clients query a Kerberos-secured Impala data warehouse safely. Private-network only, read-only by construction. Adapted from Cloudera's open-source Iceberg MCP server (Apache 2.0) and substantially reworked.

**Built and maintained by me:**
- Replaced LDAP password auth with Kerberos GSSAPI from a keytab, over binary HiveServer2 with TLS — no password setting exists anywhere in the codebase
- Hardened the read-only guard: single statement, allowlisted leading keyword, write/DDL keywords rejected anywhere in the query
- Added a result cache keyed on each table's last successful load, so answers are never stale, plus single-flight de-duplication of identical concurrent queries
- Added a connection pool, worker threads, row caps, query time limits, and a `SELECT *` guard tuned for 300+ column columnar tables
- Added streamable HTTP transport with liveness/readiness probes so the service can run stateless behind replicas, alongside stdio for jumpbox use
- Versioned JSON output contract with per-query freshness metadata; CI for tests and lint, container build, and a deployment contract for the chart owner
- 121 tests, Dockerized, live-tested on the jumpbox

`Python` `MCP` `Kerberos/GSSAPI` `Cloudera Impala` `Docker` `TLS` `GitHub Actions` `pytest`

### 🔐 Secure Data Warehouse REST API
> A contract-first Java/Spring Boot API that gives authorized consumers controlled, paginated access to a Kerberos-secured data warehouse, with scope-based access control and PII kept inside the warehouse by default.

**My role:** my tech lead built the first resource; I took it to production readiness and extended it from 1 resource to 14.
- Built a manifest-driven engine that serves 13 new resources (2,200+ columns, 250+ filters) from validated descriptors instead of hand-writing each one; the catalogue is checked at start-up and the app refuses to start on a bad entry
- Generated SQL uses only bound parameters and identifiers from that validated catalogue, so caller input never reaches a statement as text
- Cut a single-day query from ~150 s to ~5 s by pushing the date filter inside the source query, and added two-phase paging and optional column selection for very wide tables
- Fixed correctness issues before the first deploy: exact counts that always match paging, timeouts reported as 504 instead of "warehouse down", and empty tables returning an empty page
- Hardened deployment: environment configs that fail closed, a network policy that refuses to render an allow-all rule, and the keytab supplied by the cluster instead of baked into the image
- Added a one-call smoke test that reports which layer is broken (ingress, gateway headers, Kerberos, TLS or query)

`Java` `Spring Boot` `Kerberos` `Cloudera Impala` `OpenAPI` `Kubernetes` `Helm` `Bruno`

### 📡 Real-Time Road Traffic Subscriber
> A long-running Node.js service that consumes a real-time road-traffic Pub/Sub feed, transforms each message into synthetic GPS probe traces, and submits them to a downstream mapping platform. It includes a live map dashboard, health endpoints, and Prometheus metrics.

**My role:**
- Integrated a Python-based service health monitor into the service, ported from an existing internal monitor
- Fixed the Teams/WhatsApp alerting pipeline
- Stabilized data submission to the mapping platform at ~7.3 posts/sec
- Stabilized the Kubernetes staging deployment
- Kept the staging and main branches aligned, resolving merge conflicts to preserve Kong API Gateway subpath routing

`Node.js` `Koa` `Google Cloud Pub/Sub` `Docker` `Kubernetes` `Kong` `Prometheus`

### 🛰️ Geospatial Data Sync Pipelines (Airflow)
> Apache Airflow DAGs that sync large satellite-derived geospatial datasets (millions of features each) from PostgreSQL/PostGIS into a GIS visualization platform.

**My role:**
- Authored the DAGs for a new quarterly satellite dataset series (roads, buildings, greenery, centerlines, construction waste, and more), each with its own attribute mapping and filter configuration
- Diagnosed and fixed request-size failures (HTTP 413) by adding byte-aware batching and tuning the batch cap to the platform's observed 1 MB limit
- Simplified oversized geometries at the source with PostGIS topology-preserving simplification, cutting the worst-case payload from 2.37M to 594K characters
- Fixed schema, case-sensitivity, and filter-cardinality bugs that were causing silent import failures

`Apache Airflow` `Python` `PostgreSQL` `PostGIS` `SQL` `REST APIs` `Geospatial`

### 🚦 Nationwide Real-Time Traffic Pipeline
> A Python service that converts a live traffic feed covering all of Saudi Arabia into GPS probe data for a downstream mapping platform, refreshed every 5 minutes. It is containerized and deployed to OCI managed Kubernetes.

**My role:**
- Implemented a network-resilience fix for the data push after a root-cause diagnosis of silently dropped idle connections: shorter request timeouts, a hard per-wave deadline so stalled requests can't block later waves, and TCP keepalive on the HTTP connection pool
- Added configurable subpath deployment support so the service works behind the API gateway, verified end to end in Docker (including a port-handling redirect bug I found and fixed)
- Added a graduated OK / Degraded / Error status indicator to the operations dashboard, so minor partial failures are no longer shown as outages
- Ran the service locally, validated its output, and handed releases off for staging/production

`Python` `Docker` `nginx` `Kubernetes (OKE)` `Kustomize` `OCI`

### 🛠️ Kerberos Impala SQL CLI
> A Java command-line tool that lets automated jobs query a Kerberos-secured warehouse using keytab authentication, with no passwords and no `kinit`.

**My role:**
- Set up and configured the tool locally and on the jump box
- Verified end-to-end connectivity and authentication, and ran validation queries
- Handed it off for team use after sign-off

`Java` `Kerberos` `JDBC` `TLS` `CLI Tooling`

---

## 🌱 Currently

- **Cloudera Technical Professional Accreditation** (earned Aug 2026)
- Going deeper on **Kubernetes internals** and **platform engineering**
- Preparing for the **Certified Kubernetes Administrator (CKA)**
- Sharpening my **backend development** skills

---

## 🧰 Projects

- **[contact-card](https://github.com/sahilansari0797/contact-card)**: a custom, QR-scannable digital contact card, hosted on GitHub Pages.
- **[sum-service](https://github.com/sahilansari0797/sum-service)**: a simple Node.js API service for testing API environments and integration scenarios.

---

## 📫 Reach me

- **Email:** msahilansari.97@gmail.com · sahil.ansari@wedosolutions.sa
- **LinkedIn:** [in/sahilansari7](https://www.linkedin.com/in/sahilansari7/)
- **Location:** Riyadh, Saudi Arabia

---

*Always sharpening the stack.*
