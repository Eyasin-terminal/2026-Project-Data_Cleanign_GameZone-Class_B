


![Project Banner](assets/gamezone_banner.png)

# Data Integrity & Supply Chain Audit for GameZone Global

**Role:** BI Analyst
**Domain:** Global E-Commerce & Retail
**Tools:** MS Excel

---

## 📌 Project Snapshot

| Item                     | Details                                                                     |
| ------------------------ | --------------------------------------------------------------------------- |
| **Business Problem**     | Executive decisions were at risk due to unreliable, logic-broken sales data |
| **Dataset Type**         | Multi-table, enterprise-style transactional dataset                         |
| **Core Focus**           | Data Integrity, Business Logic Validation, Root Cause Analysis              |
| **Key Outcome**          | A trusted **Golden Dataset** + full audit trail                             |
| **Primary Stakeholders** | Executive Board, Supply Chain, Marketing, Web Engineering                   |

---

## 1. Business Context & Objective

### The Scenario

GameZone is a global retailer of gaming hardware operating across **online channels and physical retail stores**.
Ahead of a quarterly strategy review, the Executive Board required data-backed answers to three core questions:

* **Product Portfolio:** Which products drive the highest *revenue* vs *volume*?
* **Logistics Performance:** How efficient is order-to-delivery across regions?
* **Geographical Growth:** Which regions contribute the most sales and penetration?

### The Problem

The raw sales dataset was **structurally compromised**.
Initial validation uncovered critical logic failures—such as delivery dates occurring *before* purchase dates—making the dataset unsafe for direct analysis and executive reporting.

### The Objective

To conduct a **Data Cleaning & Logic Audit** and produce a **“Golden Dataset”** that:

* Preserves revenue integrity
* Enforces real-world business rules
* Enables confident, decision-grade analysis

---

## 2. Data Architecture & Scope

![Table Structure & Relation](assets/Tables_Structure.png)

The project simulates a **real-world, messy enterprise dataset** composed of two interdependent tables:

### Core Tables

* **Master Sales Table**
  Transaction-level data including Order ID, User ID, product details, pricing, and timestamps.

* **Regional Code Table**
  Standardized geographic mappings for countries and store locations.

### Cleaning & Audit Workflow

1. **Ingestion** – Load raw, unvalidated datasets
2. **Audit** – Build an Issue Log capturing error type, frequency, and severity
3. **Remediation** – Apply commercial and operational logic
4. **Final Output** – Analysis-ready dataset + documentation

---

## 3. Business Logic Transformation

Rather than focusing only on missing values, this project enforced **commercial reality checks**—identifying **business impossibilities**, not just data inconsistencies.

| Data Check              | Business Logic Applied                                | Commercial Impact                                            |
| ----------------------- | ----------------------------------------------------- | ------------------------------------------------------------ |
| **Logistics Logic**     | `Shipping_Date` must be later than `Purchase_Date`    | Enables accurate Order-to-Delivery KPIs for Supply Chain     |
| **Identity Logic**      | A single `Order_ID` cannot map to multiple `User_IDs` | Protects Customer Lifetime Value (CLV) and retention metrics |
| **Financial Logic**     | Transactions cannot be $0 (except valid promo cases)  | Prevents revenue under-reporting and flags checkout failures |
| **Geo-Standardization** | Country and region codes normalized                   | Enables accurate regional performance analysis and heat-maps |

---

## 4. Root Cause Analysis & Critical Findings

This section represents the **core analytical value** of the project.
Instead of deleting problematic records, I investigated **why** they existed and assessed their business risk.

---

### 🚩 Case 1: “Time Travel” Operational Glitch

**Impact:** 9.15% of total records

* **Issue**
  Delivery dates appeared *before* purchase dates.

* **Business Risk**
  Makes it impossible to reliably evaluate logistics efficiency—directly blocking Executive Question #2.

* **Decision & Action**
  Deleting 9% of transactions would distort revenue reporting.
  These records were **flagged (not removed)** in the Issue Log with guidance for downstream analysts to consult Operations before inclusion in time-based KPIs.

---

### 🚩 Case 2: “Nintendo Switch” Concurrency Bug

**Impact:** 0.7% of total records

* **Issue**
  Duplicate `Order_IDs` linked to different `User_IDs`.

* **Pattern Identified**
  Occurred **exclusively** for:

  * Product: *Nintendo Switch*
  * Channel: *Website*

* **Root Cause Diagnosis**
  Indicates a backend **race condition** during high-traffic sales (likely a flash sale), where concurrent checkout sessions were assigned the same Order ID.

* **Decision & Action**
  Flagged as a **technical system defect** and documented for the Web Engineering team to prevent future revenue attribution errors.

---

## 5. Final Deliverables

The following assets are prepared for handoff to the Analytics and BI teams:

* **✅ Golden Dataset**
  Cleaned, standardized, and ready for Power BI / Tableau ingestion
  📂 `resources/Cleaned_data_gamezone.xlsx`

* **📋 Issue Log**
  Complete audit trail documenting every anomaly, its frequency, and resolution status (Fixed vs Flagged)

* **📝 Analyst Notes**
  Guidance on how to interpret flagged records during KPI and time-series analysis

---

## 6. Skills Demonstrated

* Data Quality Auditing & Validation
* Business Rule Enforcement
* Root Cause & Pattern Analysis
* Stakeholder-Focused Documentation
* Excel-based Data Cleaning & Structuring

---

### 🎯 Portfolio Intent

This project is designed to demonstrate **real-world BI readiness**—where data is imperfect, business logic matters, and analyst decisions directly influence executive outcomes.

---

If you want, next we can:

* Create a **1-paragraph recruiter summary** for LinkedIn or resumes
* Optimize this README specifically for **ATS keyword matching**
* Add a **“Business Questions Answered”** section using the cleaned data

Just tell me the next step.
