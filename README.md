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

*Production services for public-sector platforms at WeDo Solutions. Code is private (client work). Most are designed by my tech lead; my specific role on each is listed below.*

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

### 🧩 Custom Kong API Gateway Plugins
> A repository of custom Lua plugins for the company's Kong API Gateway, packaged into a single Docker image and deployed through the Kong Ingress Controller on Oracle Kubernetes Engine.

**My role:**
- Set up the repository and its Docker packaging for Kong's plugin path conventions
- Developed a custom URL-rewriter plugin in Lua, including refactoring its response-header URL handling
- Documented the plugin structure and build process for the team

`Kong` `Lua` `Docker` `Kubernetes` `Kong Ingress Controller` `OCI`

### 🔐 Secure Data Warehouse REST API
> A contract-first Java/Spring Boot API that gives authorized consumers controlled, paginated access to a Kerberos-secured data warehouse, with scope-based access control and PII kept inside the warehouse by default.

**My role:**
- Deployed and ran the service locally against the warehouse, including Kerberos keytab-based authentication
- Validated API behavior and responses against the OpenAPI contract
- Obtained sign-off and handed the release off for staging/production deployment

`Java` `Spring Boot` `Kerberos` `Cloudera Impala` `OpenAPI` `Helm`

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
