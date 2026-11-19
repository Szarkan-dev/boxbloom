# 🌸 BoxBloom — Production Release Build

> **Intelligent Churn-Aware D2C Subscription Management Platform**  
> *Hackathon Production Release Edition*

---

## 📌 Executive Overview

**BoxBloom** is a fullstack subscription box management web application designed to combat high subscriber cancellation rates in direct-to-consumer (D2C) delivery services. By replacing rigid "all-or-nothing" cancellation portals with an adaptive, churn-aware customer experience, BoxBloom empowers subscribers to swap items, pause/skip deliveries, adjust billing cadence, and send gifts, while providing merchants with algorithmic churn risk diagnostics and retention analytics.

---

## ✨ Key Features & Architecture

### 1. 👤 Customer Subscription Portal
- **Plans & Pricing (Modules 1–2 Static Phase):** Mini ($19/mo), Classic ($39/mo), and Deluxe ($59/mo) plan tiers with transparent pricing and billing cadence toggles (Monthly, Bi-Monthly [5% off], Quarterly [10% off]). Includes responsive FAQ accordion.
- **Interactive Box Customizer (Modules 3–4 Dynamic Phase):** Real-time item swapper allowing subscribers to pick catalog items within their plan tier limit across 3 themes: *Artisan Coffee Roasters*, *Gourmet Snacks*, and *Eco-Grooming*.
- **Renewal & Delivery Tracker:** Visual countdown timer tracking packing cutoff deadlines, next billing date, and dispatch milestones.
- **1-Click Skip & Pause Controls:** Skip upcoming cycle or pause billing for 30/60 days without subscription termination.
- **Gift This Month's Box (Stretch Feature):** Redirect an upcoming box to a friend's shipping address with a custom gift message.
- **Product Feedback Rating Matrix (Stretch Feature):** 5-star item feedback score matrix to optimize future box selections.
- **Dark Mode Support & CSS Custom Properties:** Smooth CSS custom property theme switcher with dark/light mode persistence and keyframe animations.

### 2. ⚡ Churn Risk Diagnostic & Targeted Interventions
- **Weighted Heuristic Risk Scoring Engine:** Evaluates subscriber inactivity (days since login), consecutive skipped months, support sentiment score, and box tenure to calculate churn risk scores (0–100) and tiers (**Low**, **Medium**, **High**).
- **Targeted Retention Flow:** Triggers non-coercive retention incentives (e.g., 20% off next 3 boxes, free VIP bonus snack, 1-click skip) before revealing the final cancellation action.
- **Subscription Lifecycle State Machine:** Seamless state transitions: `Active` ↔ `Skipped` ↔ `Paused` ↔ `Cancelled` / `Retained`.

### 3. 📊 Merchant Subscriber Health Dashboard
- **Live Business KPIs:** Real-time metrics for Monthly Recurring Revenue (MRR), Average Revenue Per User (ARPU), Net Churn Rate, Active Subscribers, and Retention Save Rate.
- **Risk Cohort Distribution:** Visual progress breakdown of Low, Medium, and High churn risk subscriber cohorts.
- **Subscriber Cohort Table:** View all 25 pre-loaded customer accounts across 3 themes, filter by risk tier or text search, and manage profiles directly.
- **Live Retention Intervention Stream:** Auditable log of automated churn saves vs. finalized cancellations.

---

## 🛠️ Technology Stack

- **Backend:** Node.js (Built-in HTTP server with zero external npm dependencies)
- **Frontend:** HTML5, CSS3 (Custom Properties, Flexbox, CSS Grid, Animations), Vanilla JavaScript (ES6+, Fetch API, Event Loop)
- **Database:** Local JSON File Persistence (`data/seed.json`) initialized with 25 subscriber accounts across 3 themes.

---

## 🚀 Quick Start Guide

### Running the Production Server

Since the server uses standard Node.js libraries, no `npm install` is required!

1. Open your terminal in the root directory:
   ```bash
   cd boxbloom-build
   ```

2. Start the production server:
   ```bash
   node server.js
   ```

3. Open your browser at:
   ```
   http://localhost:3000
   ```

---

## 📡 REST API Reference

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/plans` | Fetch subscription plans and cadence discount tiers |
| `GET` | `/api/catalog/:theme` | Fetch item catalog for specified box theme |
| `GET` | `/api/subscribers` | Fetch list of subscribers with computed churn risk scores |
| `GET` | `/api/subscriber/:id` | Fetch detailed subscriber profile, pricing, and catalog |
| `PUT` | `/api/subscriber/:id/customizer` | Save selected box item customizations |
| `POST` | `/api/subscriber/:id/action` | Execute action (`skip`, `pause`, `resume`, `gift`, `change-cadence`) |
| `POST` | `/api/subscriber/:id/diagnose-cancellation` | Run diagnostic engine and get targeted retention offers |
| `POST` | `/api/subscriber/:id/cancel` | Finalize cancellation or record retention save offer |
| `POST` | `/api/subscriber/:id/rating` | Save 5-star product feedback rating |
| `GET` | `/api/merchant/dashboard` | Fetch merchant business metrics, MRR, risk cohorts, and logs |

---

## 📄 License & Attribution

Built for the **BoxBloom ChurnChaser Hackathon Challenge**.
