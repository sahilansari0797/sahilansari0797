# Hi, I'm Sahil 👋

**Infrastructure & DevOps Engineer** based in Riyadh — I keep production platforms reliable, observable, and easy to ship to.

I didn't start in software. I hold a **Mechanical Engineering** degree and began in CAD design (AutoCAD, SolidWorks, ANSYS), then moved into IT and GIS work on major national projects before finding my home in DevOps. That path taught me systems thinking and precision under real-world constraints — and it shapes how I approach infrastructure today: understand the whole system first, then make it robust.

---

## 🛠️ What I work with

**Orchestration & Containers:** Kubernetes (k3s), Docker \
**API & Backend:** Kong API Gateway, Node.js / Koa.js, PostgreSQL, Elasticsearch \
**Observability:** Prometheus, Grafana \
**Cloud & Data:** Oracle Cloud Infrastructure (OCI), Cloudera Data Platform (CDH) \
**Foundations:** Linux, Git, networking, Bash

---

## 💼 What I do

At **WeDo Solutions**, I'm part of the team building and running the infrastructure behind large public-sector platforms — primarily for the **Ministry of Municipal and Rural Affairs and Housing (MOMAH)**. My day-to-day spans running Kubernetes and Kong in production, building Node.js/Koa backends on PostgreSQL and Elasticsearch, and maintaining a Prometheus/Grafana observability stack that helps us catch problems before users do.

---

## 🏗️ Selected Work

*Professional projects at WeDo Solutions. Code is private (client work); summaries describe my engineering contribution.*

**Real-Time Traffic Data Platform** \
Designed and containerized a Python pipeline that ingests a live traffic API and pushes processed, downstream-ready data on scheduled cadences. Built supporting API services (viewport queries, health, stats) and an operations dashboard. Deployed to managed Kubernetes (OCI OKE) via Kustomize overlays with secrets management, automated TLS, and a pytest suite covering core invariants. \
*Python · Docker · Kubernetes (OKE) · Kustomize · OCI · REST APIs*

**Secure Data Warehouse REST API**  \
Built a read-only REST inquiry service (Java 21, Spring Boot) over a Kerberos-secured data warehouse on Cloudera Impala. Contract-first (OpenAPI 3.1) with every response schema-validated in tests; implemented keyset pagination with signed HMAC cursors, per-client rate limiting, RFC 9457 error handling, conditional GETs (ETag), and bilingual responses. Enforced scope-based access control with PII protected at the query layer. Shipped as a Helm-deployed Kubernetes service — non-root, read-only root filesystem, network policies, autoscaling, Prometheus metrics, and a GitHub Actions CI pipeline with image scanning.  \
*Java · Spring Boot · Kubernetes · Helm · Kerberos · Cloudera Impala · OpenAPI · GitHub Actions · Prometheus*

---

## 🌱 Currently

- Going deeper on **Kubernetes internals** and **platform engineering**
- Preparing for the **Certified Kubernetes Administrator (CKA)**
- Sharpening my **backend development** skills

---

## 🧰 Projects

- **[contact-card](https://github.com/sahilansari0797/contact-card)** — a custom, QR-scannable digital contact card, hosted on GitHub Pages.
- **[sum-service](https://github.com/sahilansari0797/sum-service)** — a simple Node.js API service for testing API environments and integration scenarios.

---

## 📫 Reach me

- **Email:** msahilansari.97@gmail.com · sahil.ansari@wedosolutions.sa
- **LinkedIn:** [in/sahilansari7](https://www.linkedin.com/in/sahilansari7/)
- **Location:** Riyadh, Saudi Arabia

---

*Always sharpening the stack.*
