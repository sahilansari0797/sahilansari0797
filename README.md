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

## 🏗️ Systems I've Worked On

*Production services for public-sector platforms at WeDo Solutions. Code is private (client work). These services were designed by my tech lead; my role covers local deployment, validation, and release sign-off before handoff to our deployment team for staging and production.*

### 🚦 Nationwide Real-Time Traffic Pipeline
> A Python service that converts a live traffic feed covering all of Saudi Arabia into GPS probe data for a downstream mapping platform, refreshed every 5 minutes. It is containerized and deployed to OCI managed Kubernetes.

**My role:**
- Stood up and ran the full service locally (container build, runtime configuration, dry-run mode)
- Performed functional and sanity validation of the pipeline output before release
- Obtained sign-off and handed the release off for staging/production deployment

`Python` `Docker` `Kubernetes (OKE)` `Kustomize` `OCI`

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
