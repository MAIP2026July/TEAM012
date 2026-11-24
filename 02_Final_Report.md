# VendorPulse AI: Final Report

Team: TEAM012 · Member: V V S S N Padmaji Saladi (2025mb26046) · Instructor: Vinaya Sathyanarayana

## 1. Product Strategy and Opportunity Framing

## Product vision

Every store knows which vendor is coming, when, and how far to trust that, so the dock is staffed when the truck arrives and nobody waits for a truck that is not coming.

## Jobs to be done

- **Receiving lead:** When I plan the dock schedule each morning, I want to know which small vendors will really arrive and when, so that I staff the dock at the right times and stop vendors from self-scanning.

- **Receiving associate:** When a vendor has not shown up or a truck appears unexpectedly, I want a quick answer on my handheld, so that I do not have to call the office or search several systems.

- **Vendor manager:** When I review local vendors, I want a fair, evidence-backed reliability view, so that I can start a factual conversation with a vendor who keeps missing windows.

## Who buys, who uses, who benefits

| **Role**        | **Who**                                          | **Value to them**                                           |
|-----------------|--------------------------------------------------|-------------------------------------------------------------|
| Buys (customer) | Grocery / supercenter chain, VP Store Operations | About \$5,100 saved per store a year for \$1,188            |
| Uses daily      | Receiving lead                                   | Staffing plan by 6 AM with predicted windows and risk       |
| Uses daily      | Dock associate                                   | Answers on the handheld instead of calling the office       |
| Benefits        | Vendor manager                                   | Reliability backed by delivery evidence                     |
| Benefits        | Small / local vendors                            | Less waiting at an unstaffed dock; a fair, disputable score |

## Opportunity framing

- **Why it matters:** DSD receiving is a daily, repeated decision in every store. Errors show up as idle labor, self-scan variances, wrong balance-on-hand and lost sales.

- **Why current alternatives are weak:** agreed windows are not followed by NEX vendors; spreadsheets and reports describe the past and cannot read emails or call notes; knowledge leaves with experienced leads.

- **Why AI helps:** arrival and reschedule behavior is learnable from history (vendor, weekday route, season, holidays). Language models make the answer usable at the dock and turn unstructured messages into proposed updates.

- **Product, not project:** every chain with NEX vendors has the same problem. One product serves all of them; each chain configures its vendor list, windows, thresholds and receiving data export. Nothing is custom-coded per customer.

## Will people change? Four pillars

| **Pillar** | **Assessment**                                                                                                                                               |
|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Domain     | Receiving leads and store directors are measured on labor and shrink. Carrot: fewer surprises and an easier morning. Stick: shrink audits and labor targets. |
| Technology | Feasible today: receiving timestamps already exist; the prototype shows the models beat simple baselines.                                                    |
| Regulator  | No product regulator. Vendor contact data must be kept private, and vendor scores must not trigger automated penalties (fair dealing with vendors).          |
| Behavior   | Lives inside the handheld app associates already carry; no new login or device.                                                                              |

## AI opportunity matrix

| **AI idea**                                             | **Business value**      | **Feasibility now**                 | **Priority**         |
|---------------------------------------------------------|-------------------------|-------------------------------------|----------------------|
| Arrival window + late / reschedule risk for NEX vendors | High: staffing, shrink  | High: history exists                | MVP                  |
| Vendor reliability score with evidence                  | High: vendor management | High: rule on history               | MVP                  |
| Natural-language Q&A on handheld                        | Medium-High: adoption   | High: API LLM                       | MVP                  |
| Read vendor emails / dock notes into proposed changes   | Medium                  | Medium                              | MVP (human confirms) |
| External signals (weather, traffic) + proactive alerts  | Medium                  | Medium                              | Phase 2              |
| PO, items and delivery variance answers                 | High                    | Low: needs PO/receiving integration | Phase 3-4            |
| Auto-drafted vendor performance letters                 | Medium                  | Medium; governance heavy            | Phase 5              |

## Feature prioritization (RICE)

Reach = receiving leads and associates per week in the pilot store; Impact 0.5-3; Confidence %; Effort in person-weeks. Values are team estimates.

| **Feature**                                   | **Reach** | **Impact** | **Confidence** | **Effort** | **RICE**      |
|-----------------------------------------------|-----------|------------|----------------|------------|---------------|
| Today's schedule with predicted window + risk | 12        | 3          | 80%            | 3          | 9.6           |
| Evidence and confidence on every answer       | 12        | 2          | 90%            | 1          | 21.6          |
| "Not enough data" fallback                    | 12        | 2          | 90%            | 0.5        | 43.2          |
| Reliability score (0-100)                     | 6         | 2          | 70%            | 1.5        | 5.6           |
| Natural-language Q&A                          | 12        | 1.5        | 70%            | 3          | 4.2           |
| Email / dock-note extraction with confirm     | 4         | 1.5        | 60%            | 3          | 1.2           |
| Weather / traffic signals                     | 12        | 1          | 50%            | 4          | 1.5 (Phase 2) |

*The trust features score highest because they are cheap and the pilot fails without them. Q&A ranks below the schedule view: the core value is the prediction; chat is how it reaches the dock.*

## Build vs buy vs partner/API

- **Recommended path:** API-first LLM (Azure OpenAI) with tool calling, plus our own ML models trained on each chain's delivery history.

- **Why:** existing DSD tools are built for vendors that send an ASN and do not predict NEX vendor behavior; our differentiator is the NEX-specific models and workflow fit. Building a language model adds cost and no advantage. Azure fits the Microsoft stack common in large retailers.

- **Trade-offs:** dependence on a model vendor's pricing and versions (mitigated by keeping the LLM thin and swappable behind tool APIs); in-house ML needs MLOps ownership (retraining, drift monitoring).

- **Platform vs feature:** VendorPulse is sold as its own subscription but appears inside each chain's existing store associate app, not as a separate app. It becomes a DSD platform only when later versions add PO, item and variance tools to the same copilot.

## First wedge

One paid pilot chain, up to 10 stores, small and local NEX vendors only, three questions: when will each vendor arrive, how likely are they to be late or reschedule, and how reliable have they been. No purchase orders, items, variances or vendor penalties.

## Competitive analysis

| **Alternative**                         | **Where it falls short**                                | **Our edge**                                      |
|-----------------------------------------|---------------------------------------------------------|---------------------------------------------------|
| Status quo: memory, calls, spreadsheets | No prediction; knowledge leaves with the lead           | Predicts and explains, every store, every morning |
| Agreed delivery windows                 | NEX vendors do not keep them (49% within 45 min)        | 70% in prototype; 80% is the pilot target         |
| DSD modules and vendor portals          | Need ASN/EDI; small vendors do not use portals          | Works from receiving history and vendor emails    |
| Chain builds it in-house                | 6-12 months of a data team; competes with other IT work | Live in weeks; inside the existing handheld app   |
| Offshore scheduling desk                | Reactive calls; cost grows with every store             | About \$3 per store per day, flat                 |

**Go-to-market:** regional grocery and supercenter chains of 50-500 stores first, where an in-house build is least likely. Convenience stores, also heavy on DSD, are the next market.

## Course case lens

| **Case**                             | **Similar**                                                    | **Different**                                                                                               | **What we transfer / do differently**                                                                               |
|--------------------------------------|----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Swiggy (invisible AI, ETA)           | Predicting an arrival time that drives someone else's planning | Swiggy controls its riders and has live GPS; we do not control vendors and have no live location in the MVP | Show a window, not a point time; keep AI mostly invisible inside the existing app; add live signals only in Phase 2 |
| Instacart / Tesla (lifecycle, drift) | Behavior shifts with seasons, routes and shocks                | Smaller data per vendor; drift is per vendor                                                                | Weekly retraining, per-vendor drift alerts, fall back to agreed window when data is stale                           |
| Apple Card / bias in lending         | A score can disadvantage a group unfairly                      | Vendors, not consumers; harm is commercial                                                                  | Minimum history before any score, visible components, vendor dispute path, no automated action from the score       |

## 2. PM Artifact Pack

The full PRD-lite, roadmap and metric definitions are in the Appendix. This section summarizes the decisions.

## Problem statement

Receiving leads at grocery and supercenter chains cannot reliably plan dock labor for small and local NEX vendors, because these vendors arrive outside their agreed windows and reschedule without notice. The decision we improve is the morning staffing plan and the response when a vendor changes plans.

## PRD summary

| **Item**                | **Summary**                                                                                                                                                                                                                         |
|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Problem for store teams | No reliable view of which NEX vendor is coming today, when, and how dependable they are.                                                                                                                                            |
| Core workflow           | Lead opens today's list → sees predicted window + risk → asks why for risky vendors → plans staffing → confirms or rejects AI-read vendor messages → actual arrival is logged → models retrain weekly.                              |
| AI role                 | ML predicts arrival time, late risk and reschedule risk; a transparent rule computes the reliability score; the LLM understands questions, calls these tools and explains results; the LLM extracts proposed changes from messages. |
| Data assumptions        | At least 12 months of receiving timestamps per store; vendor master and agreed schedules are accurate; reschedules and no-shows can be inferred from schedule vs receipt records.                                                   |
| Risks                   | Wrong prediction leads to wrong staffing; invented answers; unfair scores for small vendors; sensitive vendor data exposure; drift.                                                                                                 |
| Fallback logic          | Fewer than 8 past deliveries → "not enough data", plan to agreed window. Low confidence → show agreed window plus a warning. LLM or model unavailable → plain schedule list. Unclear message → route to lead, no change.            |

## MVP definition

The MVP must prove that (1) predictions beat the agreed window and a simple vendor average, (2) receiving leads and associates understand and trust the risk bands and evidence, and (3) humans can correct the AI quickly. MVP features: today and 7-day schedule with predicted window and risk, reliability score, last-90-day history, explanations, confidence, "not enough data" response, message extraction with confirm/reject, and a manual override with reason.

## Roadmap with proof gates

| **Phase**                                             | **Scope**                                                             | **Proof gate to move on**                                                                                                                                                       |
|-------------------------------------------------------|-----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0\. Prototype (done)                                  | Simulated data, ML models, copilot UI, HITL                           | Workflow and trust model are clear; model beats baselines on test data                                                                                                          |
| 1\. Build MVP + paid pilot (Jan-Jun 2027)             | 1 chain, up to 10 stores, real NEX history, live copilot on handhelds | ≥80% arrivals within ±45 min; ≥40% of late or no-show deliveries planned for in advance; ≥90% grounded answers, 0 invented numbers; unstaffed arrivals and self-scans down ≥25% |
| 2\. Chain rollout + better predictions (from Q3 2027) | Weather, traffic, holidays, proactive alerts                          | Accuracy holds across store types; alert precision ≥60%                                                                                                                         |
| 3\. Purchase orders                                   | PO and expected items per delivery                                    | PO data quality; answers correct ≥95%                                                                                                                                           |
| 4\. Delivered items and variances                     | Receiving data, digitized NEX invoices                                | Variance detection validated by Inventory Control                                                                                                                               |
| 5\. Vendor performance                                | Accuracy, shrink, chargebacks; drafted vendor letters                 | Governance sign-off; human approval on every vendor communication                                                                                                               |

## Success metrics

- **Product:** share of mornings the lead uses VendorPulse to plan; questions answered without escalation.

- **Model:** arrivals within ±45 min of prediction; how often late and reschedule risk is ranked correctly (ROC-AUC); precision/recall of the High-risk band.

- **Business:** unstaffed vendor arrivals per week; vendor self-scan events; receiving idle hours; count variances.

- **Trust / guardrail:** grounded-answer rate; invented numbers (must be zero); override rate; extraction errors caught at confirmation.

## How these artifacts change because the product is AI-powered

| **Artifact**      | **What changed for VendorPulse**                                                                                     |
|-------------------|----------------------------------------------------------------------------------------------------------------------|
| Problem statement | Names the decision being improved (morning staffing plan), not just a pain point.                                    |
| User stories      | Include what the lead or associate sees when the model is unsure or has no data, and the cost of a wrong prediction. |
| PRD               | Adds data assumptions, minimum-history rule, confidence logic and fallbacks.                                         |
| Roadmap           | Phases are proof gates with thresholds, not only feature releases.                                                   |
| Metrics           | Model metrics (accuracy, AUC) are tied to business metrics (unstaffed arrivals, self-scans).                         |
| Launch checklist  | Requires review, rollback to plain schedule, and an escalation path.                                                 |
| Pricing note      | Prices on value per store, carries the AI cost, and checks cost to serve per store per month.                        |

## 3. UX, Workflow and Trust Design

## Main workflow (swimlane)

![figure](Appendix/Wireframes/swimlane_workflow.png)

*Figure 1. Who does what. Yellow = AI step (probabilistic); teal = a person decides. Source: Appendix/Wireframes/swimlane_workflow.puml*

| **Step**                                       | **Type**             | **Gated or straight through**                                  | **How uncertainty is shown**                                                |
|------------------------------------------------|----------------------|----------------------------------------------------------------|-----------------------------------------------------------------------------|
| AI1-2 · arrival window, late / reschedule risk | ML, probabilistic    | Straight through to the lead's list; the lead decides staffing | Window, risk band, probability, confidence, evidence                        |
| AI3 · read vendor email / note / voicemail     | LLM, probabilistic   | Gated: nothing changes until the lead confirms                 | Original text beside extracted fields; low confidence can only be escalated |
| AI4 · answer questions on the handheld         | LLM, probabilistic   | Straight through, read-only; numbers only from data tools      | Tools used, data behind the answer, confidence                              |
| Reliability score                              | Rule (deterministic) | Gated: lead reviews before the vendor manager sees it          | Components and number of deliveries; minimum 8                              |
| Weekly retrain                                 | Scheduled job        | No decision made                                               | Accuracy report per vendor                                                  |

## Key screens (from the working prototype)

- **Today:** vendors sorted by predicted arrival, each with window, risk chip, confidence, three evidence lines and an Override button.

- **Ask the copilot:** answers show the tools called, the data used and a confidence level.

- **Vendor messages:** original text next to the extracted change; Confirm / Reject; low-confidence items can only be sent to the lead.

- **Vendor scores:** 0-100 score with its four components; "not enough data" for new vendors.

- **Model evidence:** how the model compares with the agreed window and a simple average.

![figure](Appendix/Screenshots_or_Video/01_today_and_copilot.png)

*Figure 2. Today view and copilot (prototype, simulated data). More screens in Appendix/Screenshots_or_Video.*

## Trust and explainability

| **What store teams need to know**                        | **Must be visible**                                                                                | **Should be hidden**                                                |
|----------------------------------------------------------|----------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| When the vendor will probably arrive and how sure we are | Predicted window, risk band, probability, confidence, "late on 5 of last 8 Fridays"-style evidence | Model internals, feature weights, raw probabilities beyond 2 digits |
| Whether a score is fair                                  | Score components and the number of deliveries behind it                                            | Scores from dock associates' view (leads and Merchandising only)    |
| What the AI read from a message                          | Original message beside the extracted fields                                                       | Sender personal details beyond what is needed                       |

## Uncertainty handling

- **High confidence** (8+ same-weekday deliveries, stable arrival times): show the predicted window and risk directly.

- **Medium / low confidence:** show the window with a confidence tag and evidence; recommend a buffer for High-risk vendors.

- **Not enough data** (fewer than 8 deliveries): no prediction or score; plan to the agreed window. The copilot says so instead of guessing.

- **Failure / fallback:** if the LLM or model service is down, the app shows the plain agreed schedule. Out-of-scope requests (POs, chargebacks) get a clear refusal that points to the owner.

## Human-in-the-loop

- The lead decides staffing; predictions only inform it.

- Any schedule change read from an email, note or voicemail needs a person to confirm it. Nothing is applied automatically.

- Leads can override any prediction with a reason ("vendor called, arriving 10:30"); overrides are logged and used to review the model.

- Scores are reviewed by the lead before they reach Merchandising; business actions on vendors stay with Merchandising and Vendor Management.

## 4. Data, Model and Evaluation Strategy

## Problem as AI tasks

| **Task**                                      | **Type**                                                | **Method in prototype**                                                       |
|-----------------------------------------------|---------------------------------------------------------|-------------------------------------------------------------------------------|
| Arrival time for a scheduled delivery         | Regression (forecast)                                   | Gradient-boosted regressor (absolute-error loss); window = prediction ±45 min |
| Late arrival (after the agreed 2-hour window) | Binary classification                                   | Logistic regression                                                           |
| Reschedule or no-show                         | Binary classification                                   | Logistic regression                                                           |
| Vendor reliability score                      | Scoring rule                                            | 40% on-time, 25% reschedule, 20% no-show, 15% count variance, last 90 days    |
| Answer questions                              | Generation with tool calling (RAG over structured data) | Simulated by an intent router; production = Azure OpenAI                      |
| Read vendor messages                          | Information extraction                                  | Simulated (pre-filled extractions); production = LLM with confidence          |

## Data sources

- **Internal:** receiving transaction timestamps and status, vendor master, agreed delivery days and windows, reschedule records, count variances at receiving.

- **External (Phase 2):** weather, traffic, holidays, local events.

- **Generated by store teams and vendors:** vendor emails, dock notes, voicemail transcripts, overrides with reasons.

## Data assumptions and the simulated dataset

Real retailer data cannot be used in a course submission, so the prototype uses a simulated history for one store: 25 fictional NEX vendors, 18 months (May 2025 to Nov 2026), 3,098 past scheduled deliveries plus 42 scheduled for the coming week. The simulation encodes patterns observed in NEX receiving: each vendor has its own habitual arrival offset per weekday route, one weekday that runs late, more delay and rescheduling around holidays and in winter, and different reliability profiles. Two vendors were onboarded recently to test the "not enough data" path. The real pilot must confirm these patterns.

## Labels / ground truth

Labels come from the receiving system, so no manual labeling is needed: actual arrival time minus agreed window start gives the arrival offset; arrival after the window end = late; a scheduled delivery with no receipt and a later receipt within 3 days = rescheduled; no receipt = no-show. In the pilot, receiving leads confirm ambiguous cases weekly, and confirmed message extractions become labeled examples for the extraction prompt.

## Baselines

- **Agreed-window rule:** assume the vendor arrives at the start of the agreed window (today's practice).

- **Vendor recent average:** median of the vendor's last 10 arrivals, and the vendor's 90-day late / reschedule rate as risk (what a dashboard would show).

## Model / API choice

Logistic regression was chosen for the risk models because it matched gradient boosting on the test set (late AUC 0.761 vs 0.741; reschedule AUC 0.705 vs 0.586) and is easier to explain and audit. Gradient boosting is used for arrival time, where it was more accurate. The reliability score is a rule on purpose: vendors and managers must be able to see exactly how it is calculated. The LLM is API-based and never computes numbers.

## Evaluation results (simulated data, time-based split)

Training: 2025-05-19 to 2026-05-30 (2019 rows). Test: 2026-06-01 to 2026-11-05 (884 rows).

| **Metric**                                        | **Agreed-window rule** | **Vendor recent average** | **ML model** |
|---------------------------------------------------|------------------------|---------------------------|--------------|
| Arrivals within ±45 min                           | 49%                    | 63%                       | 70%          |
| Mean absolute arrival error                       | 70.7 min               | 47 min                    | 41.5 min     |
| Late arrivals ranked correctly (ROC-AUC)          | n/a                    | 72% (0.719)               | 76% (0.761)  |
| Reschedules / no-shows ranked correctly (ROC-AUC) | n/a                    | 64% (0.635)               | 71% (0.705)  |
| Top 20% flagged: precision / recall               | n/a                    | 54% / 40%                 | 57% / 41%    |

*"Ranked correctly" is the ROC-AUC score shown as a percentage: take one delivery that turned out late and one that was on time; it is the chance the model gave the late one the higher risk score. 0.5 (50%) is a coin flip, 0.7 is useful, 0.8 is strong.*

![figure](Appendix/Metrics/model_vs_baseline.png)

*Figure 3. Model vs baselines. Right: High-risk deliveries were 5x more likely to have a problem than Low-risk ones.*

**What this shows:** the model clearly beats the agreed-window rule and moderately beats a simple vendor average. The risk bands separate deliveries well. **What it does not show:** real-world accuracy. Arrival accuracy (70%) is below the 80% target, so the pilot is needed and Phase 2 signals may be required.

## Evaluation framework

| **Metric type**   | **Metric**                                                                                                 | **Why it matters**                                                 |
|-------------------|------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| Technical         | % arrivals within ±45 min; MAE; risk ranked correctly (ROC-AUC); precision/recall of High band             | Staffing plans depend on the window being right                    |
| Technical (LLM)   | Grounded-answer rate on a 100-question test set; extraction precision                                      | Wrong numbers on a handheld lead to wrong actions                  |
| Business          | Unstaffed arrivals/week; self-scan events; idle receiving hours; count variances                           | These are the cost and shrink drivers                              |
| Trust / guardrail | Invented numbers (must be 0); override rate; % answers with evidence; trust survey of leads and associates | Adoption fails without trust; high overrides signal model problems |

## Launch thresholds (pilot → scale)

- Arrivals within ±45 min ≥80% on real pilot data, and better than the vendor-average baseline.

- Late arrivals ranked correctly at least 70% of the time (ROC-AUC ≥0.70); High-band problem rate at least 3x the Low band.

- ≥90% of test questions answered correctly and grounded; zero answers with invented numbers.

- Extraction precision ≥95% on confirmed changes; nothing applied without confirmation.

- Unstaffed arrivals and self-scan events down ≥25% versus the 4-week pre-pilot baseline; ≥70% of mornings planned with the tool.

- ≥40% of late or no-show deliveries planned for in advance: the share of late, rescheduled or no-show deliveries that the receiving lead acted on (called the vendor, moved staff, added a buffer or overrode the plan) before the delivery window, because VendorPulse flagged the risk or a confirmed vendor message changed the schedule.

## 5. Business, Economics and Scaling

Two separate calculations: why a chain buys (customer ROI) and why an investor funds us (startup plan). All inputs are planning assumptions; the live model with formulas is Appendix/Metrics/VendorPulse_Business_Model.xlsx.

## Monetization model

- **Subscription:** \$99 per store per month, annual contract. We price on value per store, not on tokens, because the chain pays for outcomes.

- **Paid pilot:** \$25K for up to 10 stores for 10 weeks, credited to the year-1 contract.

- **Who pays for AI:** we do. LLM and ML costs are inside the subscription; customers do not bring their own API keys. A fair-use cap of 60 questions per store per day protects the margin if usage spikes.

## Customer ROI (why the chain buys)

| **Per store, per year**                           | **Base**  | **Stress test** |
|---------------------------------------------------|-----------|-----------------|
| Loaded receiving labor                            | \$20 / hr | \$16 / hr       |
| Late or no-show deliveries planned for in advance | 50%       | 30%             |
| Idle-wait labor saved                             | \$3,058   | \$1,468         |
| Self-scan shrink avoided                          | \$2,080   | \$1,248         |
| Total savings                                     | \$5,138   | \$2,716         |
| VendorPulse price                                 | \$1,188   | \$1,188         |
| Return on price                                   | 4.3x      | 2.3x            |

Inputs: 42 NEX deliveries a week per store, 28% late or rescheduled, 30 minutes wasted on each; 2 vendor self-scans a week at about \$40 shrink each. Price is 23% of base savings, inside the 18-25% customers typically accept. The stress case stays positive but under the 3x return customers expect, so the pilot must show at least 40% of late or no-show deliveries planned for in advance; that keeps the return at 3x or more even at \$16 an hour. A 300-store chain pays \$356K a year and saves about \$1.5M.

**Planned for in advance** is the share of late, rescheduled or no-show deliveries that the receiving lead acted on (called the vendor, moved staff, added a buffer or overrode the plan) before the delivery window, because VendorPulse flagged the risk or a confirmed vendor message changed the schedule. Measured in the pilot from the action log: problem deliveries with a lead action logged before the window ÷ all problem deliveries.

## Cost to serve and unit economics

| **Per store, per month** | **Cost** | **Assumption**                                                                                         |
|--------------------------|----------|--------------------------------------------------------------------------------------------------------|
| LLM usage                | \$4.50   | 40 questions + 10 vendor messages a day at ~\$0.003 per call (verify against current provider pricing) |
| ML scoring and hosting   | \$1.50   | Nightly batch scoring, storage                                                                         |
| Support and onboarding   | \$8.00   | Largest cost to serve                                                                                  |
| Cost to serve            | \$14.00  | Price \$99 → \$85 margin (86%)                                                                         |

**Latency / cost / quality trade-off:** predictions are computed overnight, so a question is a cheap lookup plus a short answer from a small model; a larger model is used only for unclear vendor messages. This keeps answers under 3 seconds and the AI cost under \$5 per store per month.

## Startup plan (why invest)

| **Year** | **Chains**   | **Avg stores live** | **Revenue** | **Costs** | **Net**  | **Team** |
|----------|--------------|---------------------|-------------|-----------|----------|----------|
| 1 · 2027 | 2 pilots → 1 | 40                  | \$74K       | \$553K    | (\$480K) | 3        |
| 2 · 2028 | 3            | 500                 | \$594K      | \$1.11M   | (\$520K) | 5        |
| 3 · 2029 | 6            | 1,500               | \$1.78M     | \$1.77M   | +\$10K   | 7        |
| 4 · 2030 | 10           | 3,000               | \$3.56M     | \$2.46M   | +\$1.10M | 9        |

Costs: team at about \$150K loaded per person, sales and marketing (\$60K rising to \$450K), G&A (\$40K to \$160K) and the \$14 per store per month to serve. Break-even is about 1,500 stores live (\$1.52M fixed costs ÷ \$1,020 contribution per store a year). Year 4's 3,000 stores are 6.6% of the 45,575 US supermarkets counted by FMI.

**The ask:** a \$1.5M seed round. The deepest cumulative loss is about \$1.0M at the end of year 2, leaving a \$500K buffer.

## Pilot scenarios (conditional plan)

| **Pilot result** | **Condition**                                                                                 | **Next step**                                                        |
|------------------|-----------------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| Success          | ≥80% of arrivals within ±45 min and ≥40% of late or no-show deliveries planned for in advance | Roll out across the chain; sign chain 2                              |
| Conditional      | 70-80% accuracy or 25-40% planned for in advance                                              | Add weather and traffic signals, second pilot, outcome-based pricing |
| Fail             | Not better than a simple vendor average                                                       | Stop; loss capped at about \$250K (first six months)                 |

## Scaling risks

- **Latency:** answers must return in under 3 seconds on store Wi-Fi; precompute predictions nightly and cache today's list on the device.

- **Cost growth:** heavy usage raises LLM cost; the fair-use cap, small-model routing and token limits keep cost to serve near \$14.

- **Provider rate limits:** agree volume limits with the LLM provider before rolling out to large chains.

- **Workflow complexity:** stores differ in dock layout and staffing; roll out in waves by store type.

- **Governance burden:** vendor scores across many stores need a review owner and a dispute process at each chain.

## 6. Ethics, Governance and Risk Note

## Main risks

- **Unfair vendor scores (bias):** small local vendors may look unreliable because of their size or lack of digital tools, not performance.

- **Hallucinated or wrong answers:** a wrong time or score leads to poor staffing or an unfair vendor conversation.

- **Privacy and commercial sensitivity:** vendor performance and schedules are confidential; messages contain personal contact details.

- **Misuse:** using scores to penalize vendors automatically, or to evaluate associates.

- **Over-reliance and drift:** staff stop applying local knowledge; vendor behavior changes over seasons and routes.

## Harm scenarios

- A local vendor gets a low score from few deliveries and loses shelf space without a fair hearing.

- The copilot states a wrong arrival time; the dock is unstaffed and the vendor self-scans, creating shrink.

- A dock associate sees another vendor's performance data and shares it.

## Controls

- **Guardrails:** the LLM answers only from tool results; numbers must come from tools; refuses out-of-scope topics (POs, chargebacks, penalties); minimum 8 deliveries before any prediction or score.

- **Review process:** human confirmation for every schedule change from messages; lead reviews scores before sharing; vendors can see and dispute their score components.

- **Escalation path:** low-confidence extractions go to the receiving lead; repeated low scores go to Vendor Management, who decide any action.

- **Access:** role-based access; dock associates see schedule and risk only; scores visible to leads and Merchandising.

- **Logging / auditability:** every answer logs the question, tools called, data version and model version; every override and confirmation is logged with the person and reason.

- **Monitoring:** weekly accuracy and drift report per vendor; score distribution checked by vendor size.

## Launch blockers

- Any answer in the test set that contains a number not returned by a tool.

- Arrival accuracy below the vendor-average baseline on real pilot data.

- Scores for small vendors systematically lower than their on-time data supports.

- No named owner for score review and vendor disputes.

## 7. Prototype / MVP

| **Item**                   | **Detail**                                                                                                                                                                                                                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Prototype type             | Web app (single page, works on a handheld screen) + Python ML pipeline. LLM layer is Wizard-of-Oz: an intent router stands in for Azure OpenAI so the demo runs without an API key.                                       |
| What it demonstrates       | The morning planning loop: today's vendors with predicted window and risk, evidence, confidence, "not enough data", vendor scores, Q&A with tool trace, message extraction with confirm/reject, and override with reason. |
| AI role                    | Real trained ML models produce every prediction; the LLM role (understanding and explaining) is shown through the tool-calling pattern.                                                                                   |
| What it does not yet prove | Accuracy on real data; real LLM answer quality and hallucination rate; handheld performance on store Wi-Fi; integration with the receiving system; adoption by receiving leads.                                           |
| Links                      | Live demo: https://claude.ai/artifact/7Si4qbkxUE6fwvSwYqg6vv (share before submitting). Code: Prototype folder (README explains how to run). Screenshots: Appendix/Screenshots_or_Video.                                  |

## 8. Recommendation

**Pilot.** The problem is real, repeated and measurable, and AI is the right lever because the decision depends on predicting vendor behavior, not listing it. The prototype shows the model beats today's rule and that the human-in-the-loop design is practical. The customer return is about 4x in the base case, and the business breaks even at about 1,500 stores. Accuracy on simulated data is below the 80% target, so we ask for a \$1.5M seed round and one 10-week paid pilot with a regional chain. Scale only if the pilot meets the success thresholds in Section 5; stop if the model cannot beat a simple vendor average on real data.
