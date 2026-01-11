# UserFunnelIQ – Retention & Lifecycle Analytics

UserFunnelIQ is an end-to-end user analytics project that mirrors how real product and growth teams analyze user behavior across the full lifecycle.

The project works on raw event-level data and answers three core business questions:

1. How well do users retain over time? (D1 → D90)  
2. Where do users drop off in the onboarding journey?  
3. What behavioral differences separate retained users from churned users?

All analysis is built using SQL-style transformations inside Python, simulating real-world analytics workflows.

---

## 📁 Data Model

The project operates on event and entity tables including:

- `users` – user profiles and signup dates  
- `app_sessions` – session start times and durations  
- `activity_data` – manual user actions inside the app  
- `subscriptions` – subscription start and cancellation events  

From these, a **cohort** is defined as:

> Users who signed up 90–120 days before the latest available date.

This allows consistent tracking from Day 1 to Day 90.

---

## 🔍 Core Analyses

### 1. Absolute Retention (D1–D90)

- Builds a unified activity layer by combining:
  - App sessions longer than 30 seconds  
  - Manually recorded activities  
- Calculates how many distinct users return on:
  - Day 1  
  - Day 7  
  - Day 15  
  - Day 30  
  - Day 60  
  - Day 90  

This shows *how engagement decays over time* for a fixed cohort.

---

### 2. Retention Checkpoint Funnel

Instead of treating each day independently, this section models **progressive retention**:

Signup
   ↓
Active on D1
   ↓
Active on D7
   ↓
Active on D30
   ↓
Active on D90

This answers:  
**“How many users truly survive through the lifecycle?”**

---

### 3. Onboarding Funnel & Activation

Tracks how users move after signup:

- Signup  
- First app session  
- First meaningful interaction  

Computes:

- Activation rate by age group  
- Average & median time to first session  
- Interaction rate across cohorts  

This identifies where early drop-offs happen and whether delays in first interaction impact retention.

---

### 4. Churned vs Retained Behavior (First 30 Days)

Users are labeled:

- **Churned** – canceled within 30 days  
- **Retained** – stayed beyond 30 days  

Within the first 30 days only, the project compares:

- Days interacted  
- Days with activity recorded  
- Average and median session gaps  
- Session durations  
- Notification opt-in behavior  

This isolates *early behavioral signals* that correlate with long-term retention.

---

### 5. Feature Usage Analysis

Summarizes how retained vs churned users differ in:

- Events per user  
- Distinct features used  
- Sessions per user  
- Session duration  

This helps answer:

> “Which types of engagement actually matter for retention?”

---

### 6. Anomaly Detection

Identifies a real data issue:

- Some users continue generating app events *after canceling their subscription*

The notebook quantifies:

- Total users who canceled within 30 days  
- How many were still active afterward  
- Percentage of post-cancellation activity  

This mimics real analyst work: discovering data or product inconsistencies.

---

## 🛠 Tools & Approach

- Python (Pandas, DuckDB)  
- SQL-style CTE-heavy queries  
- Cohort modeling  
- Funnel construction  
- Time-based lifecycle analysis  
- Behavioral segmentation  

---

## 🎯 What This Project Demonstrates

- Ability to work with raw event data  
- Strong SQL-style analytical thinking  
- Cohort and lifecycle modeling  
- Funnel construction  
- Translating events into product insights  
- Identifying both patterns *and anomalies*  

This project reflects how real analytics teams in consumer tech and fintech evaluate user behavior, activation, and retention over time.

---

## 📦 Data Note

The full raw dataset and DuckDB database are provided in compressed form due to GitHub file size limits.

In production analytics environments, raw data typically lives in data warehouses rather than in version control.  
This repository mirrors that practice by focusing on transformation logic, cohort definitions, and analytical methodology.

---
### Author 
   JYOTI KHATRI 
