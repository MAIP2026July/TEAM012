# VendorPulse AI — Milestone 1: Topic and Strategy Fix

Nov 3, 2026 · @Surya

**Course Title:** Management of AI Products

**Course No(s):** MBA ZG583

**Content:** Experiential Learning Assignment / Capstone

**Instructor:** Vinaya Sathyanarayana

| Field | Details |
| --- | --- |
| Team Name | \[TEAM###\] |
| Team Members | Surya Saladi — \[BITS ID\] |
| Date | 03/11/2026 |

## Working Title

VendorPulse AI: A Generative AI Copilot for Vendor Direct Store Delivery (DSD) Scheduling, Vendor Scoring, and Arrival-Delay and Reschedule Prediction.

## Industry / Function

Retail (Supercenter / Grocery) / Store Receiving Operations / Vendor Direct Store Delivery (DSD) / Merchandising and Vendor Management.

## Target User

- Store Receiving Team Members (on handheld devices at the receiving dock)
- Store Directors and Receiving Leads (planning labor and dock schedules)
- Merchandising and Vendor Management Teams
- Inventory Control and Loss Prevention Teams
- Store Operations Leadership

## Current Workflow Problem

A Mid-West supercenter retail chain with about 300 stores and more than $20B in revenue receives a large share of its products through Vendor Direct Store Delivery (DSD). In DSD, suppliers deliver directly to the store instead of through a distribution center. Large vendors send an Advanced Shipping Notice (ASN) through EDI before they arrive, so stores know what is coming and when.

Small and local vendors follow the NEX process (No ASN, receive everything manually). They often arrive without prior notice, at irregular times, and sometimes reschedule or skip a planned delivery without telling the store. Store receiving teams have no reliable view of which vendor is coming today, at what time, or how dependable that vendor has been in the past.

Today, store directors and receiving leads plan dock staffing from memory, emails, phone calls and spreadsheets. When a vendor arrives unexpectedly and no team member is free, vendors sometimes scan their own pallets, which creates miscounts, variances and shrink. Years of historical delivery data (timestamps, vendor IDs, delays, reschedules, variances) already exist, but it is spread across receiving, merchandising and inventory systems and is not used to plan the day.

## Why This Matters

This problem has significant operational and financial impact because:

- Unplanned vendor arrivals leave the dock unstaffed, which leads to vendor self-scanning, miscounts and shrink.
- Receiving labor is wasted when staff wait for vendors who arrive late, reschedule or do not show up.
- Inaccurate receiving data makes balance-on-hand wrong, which delays shelf replenishment and loses sales.
- Vendor reliability is judged informally, so chronically late or inaccurate vendors are not flagged to merchandising.
- Store teams cannot get quick answers on a handheld at the dock; they have to call, email or search several systems.
- When experienced receiving leads move roles, their knowledge of “which vendor comes when” is lost.

Giving store teams a reliable daily view of expected vendors, their reliability, and their likelihood of delay or rescheduling can improve dock staffing, reduce shrink and variances, and create the data foundation for wider AI use across DSD.

## Proposed AI Role

A Generative AI copilot for store receiving teams that combines Machine Learning (ML) predictions with a Large Language Model (LLM) conversational interface. The LLM answers questions using Retrieval-Augmented Generation (RAG) and tool calls over vendor schedule data, historical delivery data and ML model outputs, so every answer is grounded in the retailer's own data.

The solution will:

- Show which DSD vendors are expected at a store today or this week, with a predicted arrival window.
- Predict each vendor's likelihood of arriving late, rescheduling, or not showing up, using ML models trained on historical delivery timestamps, day of week, season, holidays and vendor patterns.
- Calculate a vendor reliability score from on-time rate, reschedule frequency, no-show rate and past delivery variances.
- Answer natural-language questions from a handheld or desktop, such as “Which vendors are likely to be late this afternoon?” or “How often has Vendor X rescheduled in the last 90 days?”
- Explain every prediction and score in plain English, with the supporting history (for example, “late on 6 of the last 8 Monday deliveries”).
- Read unstructured vendor communications (reschedule emails, call notes, dock comments) to update the expected schedule.

## Why AI Instead of a Simpler Alternative

An Excel file or a dashboard can list past deliveries and filter them, but it cannot predict what will happen today. It shows that a vendor was late before; it cannot estimate the probability that the vendor will be late or reschedule this afternoon.

Rule-based schedules assume vendors follow their agreed delivery windows. Small and local NEX vendors do not, so fixed rules break down. Spreadsheets also cannot read reschedule emails, call notes or free-text dock comments, and they require users to know which filter to apply. That is not practical for a team member standing at the dock with a handheld.

The AI-based copilot can:

- Learn each vendor's real arrival and reschedule patterns from historical data, instead of relying on agreed windows.
- Produce probabilities (likely late, likely to reschedule) that support staffing decisions, not just historical lists.
- Combine structured history with unstructured signals such as vendor emails and dock notes.
- Let users ask questions in plain language and get a short, explained answer on a handheld device.
- Scale consistently across 300 stores and thousands of vendor deliveries per week.

Standard views (today's vendor list, vendor score history) will still be available on a dashboard. The copilot adds prediction, explanation and question-answering where filtering alone does not solve the problem.

## Human-in-the-Loop Design

The system is a decision-support assistant for planning, not an autonomous scheduler or vendor-rating authority.

Human reviewers will remain responsible for:

- Deciding dock staffing and receiving plans based on the copilot's predicted arrival windows and delay risk.
- Confirming or correcting vendor schedule changes that the AI reads from emails or notes before the schedule is updated.
- Reviewing vendor reliability scores before they are shared with merchandising or used in vendor discussions.
- Overriding a prediction when local knowledge contradicts it (for example, a known road closure or a vendor's phone call).
- Escalating repeated low-score vendors to Merchandising and Vendor Management, who decide any business action.

Every answer will show its supporting evidence (delivery history behind a score or prediction) and a confidence level (High / Medium / Low). When data is insufficient, the copilot will say so instead of guessing. No vendor penalty, chargeback or contract decision will be made by the AI.

## Smallest Credible MVP

A web and mobile-friendly chat prototype for one pilot store, using historical (or simulated) DSD delivery data for 20–30 small and local NEX vendors. A user can ask questions and receive:

1. Today's and this week's expected vendor schedule, with a predicted arrival window for each vendor.
2. A vendor reliability score (0–100) built from on-time rate, reschedule frequency, no-show rate and delivery variance history.
3. The likelihood of each vendor arriving late or rescheduling (High / Medium / Low risk, with a probability).
4. Past delay and reschedule behavior for a vendor on request (for example, last 90 days).
5. A plain-English explanation and the supporting history behind every score and prediction.
6. A clear “not enough data” response when a vendor has too little history to predict reliably.

The MVP focuses only on vendor schedule, vendor score, and arrival-delay and reschedule likelihood for a single store. It does not cover purchase orders, items, variances or vendor performance analytics beyond the score.

## MVP Scope and Future Roadmap

The long-term vision is a single DSD copilot that answers any question about a vendor delivery. This project delivers Phase 1 only; later phases extend the same copilot to new data domains.

| Phase | What the copilot answers | New data needed | In this project? |
| --- | --- | --- | --- |
| Phase 1 — MVP | Vendor schedule, arrival window, reliability score, delay and reschedule likelihood, past delay behavior | Historical delivery timestamps, vendor master, delivery schedules, reschedule records | **Yes** |
| Phase 2 | More accurate predictions using external signals; proactive alerts (“Vendor X likely 45 min late”) | Weather, traffic, holidays, local events, real-time vendor updates | No — roadmap |
| Phase 3 | Purchase orders and expected items for each delivery | Merchandising PO data, ASN/EDI feeds | No — roadmap |
| Phase 4 | Delivered items and order-vs-delivery variances | Receiving data, digitized NEX invoices | No — roadmap |
| Phase 5 | Full vendor performance (accuracy, shrink, chargebacks) and drafted vendor communications | Inventory, loss prevention and finance data | No — roadmap |

## Build vs Buy vs API View

Recommendation: API-first LLM with RAG and tool calling, plus custom ML prediction models built on a managed ML platform (Microsoft Azure, aligned with the retailer's existing Microsoft stack).

Why:

- Existing LLM APIs (for example, Azure OpenAI) provide enough language understanding and summarization for the MVP; building a foundation model is unnecessary.
- The main value is in the retailer's own vendor delivery history, so the arrival, delay and reschedule prediction models are built in-house on Azure Machine Learning.
- The LLM never calculates scores or predictions itself. It calls the ML models and data services as tools and explains their outputs, which reduces hallucination risk.
- An API-first approach reduces development effort, cost and time-to-value, and lets the team focus on data quality, model accuracy and the store user experience.
- The architecture can later expand to PO, item, variance and vendor performance data (roadmap Phases 3–5) by adding new data tools, without rebuilding the copilot.

## Main Risks

- Incomplete or inconsistent historical NEX delivery records, reducing prediction accuracy during the initial rollout.
- Hallucinated or incorrect answers (for example, a wrong arrival time or score) leading to poor staffing decisions.
- Unfair vendor scores: small vendors may look unreliable only because they had no digital tools, not because they perform poorly.
- Over-reliance on predictions without store staff applying local knowledge.
- Exposure of commercially sensitive vendor data (schedules, performance) to users who should not see it.
- Model drift as vendor behavior, seasons and routes change over time.

## Success Evidence

The solution will be considered successful if it demonstrates:

- Predicted arrival windows that match actual arrival for at least 80% of recurring vendor deliveries (within a 45-minute window).
- Accurate identification of likely late or rescheduled deliveries (measured by precision and recall against actual outcomes).
- Fewer unplanned or unstaffed vendor arrivals at the pilot store, and fewer vendor self-scan events.
- Reduced receiving labor idle time spent waiting for vendors.
- Copilot answers that are correct and grounded in data for at least 90% of a test question set, with no unsupported answers.
- Positive feedback from store directors and receiving teams on usefulness and trust in the copilot.

## Team Recommendation

Proceed

The team recommends proceeding with an MVP focused on vendor schedule, vendor reliability score, and arrival-delay and reschedule prediction for small and local DSD vendors. The problem is business-critical, is supported by years of existing delivery data, has measurable labor and shrink-reduction value, and builds the foundation for a wider DSD copilot covering purchase orders, items, variances and vendor performance, while keeping humans in control of every decision.
