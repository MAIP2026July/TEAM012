# VendorPulse AI: Executive Summary

A GenAI copilot for Vendor DSD scheduling, vendor scoring and arrival-delay / reschedule prediction. Team: TEAM012 · Member: V V S S N Padmaji Saladi (2025mb26046) · Instructor: Vinaya Sathyanarayana

## Problem

US grocery and supercenter chains receive a large share of products through Vendor Direct Store Delivery (DSD). Large vendors send an Advanced Shipping Notice (ASN), but small and local vendors follow the NEX process: no ASN, irregular arrival times, and reschedules or no-shows with little notice. Receiving leads plan dock staffing from memory, phone calls and spreadsheets. The problem comes from our own work on DSD receiving at a 300-store supercenter chain.

- Unplanned arrivals find the dock unstaffed, so vendors scan their own pallets. This causes miscounts, variances and shrink.

- Associates wait for vendors who arrive late or do not come, which wastes receiving labor.

- Years of delivery history exist in receiving systems but are not used to plan the day.

## Who buys and who uses it

| **Role**      | **Who**                                            | **What they get**                                             |
|---------------|----------------------------------------------------|---------------------------------------------------------------|
| Buys          | Grocery / supercenter chain (VP Store Operations)  | Lower receiving labor and shrink across all stores            |
| Uses daily    | Receiving lead; dock associate on a Zebra handheld | Who is coming, when, and how sure we are                      |
| Also benefits | Vendor manager; the vendors                        | Fair evidence on reliability; shorter waits at a staffed dock |

## Product concept

**VendorPulse AI** is a receiving copilot for small and local DSD vendors, sold to grocery and supercenter chains as a per-store subscription. For each store it shows which vendors are expected today and this week, a predicted arrival window, the risk that each vendor is late or reschedules, and a 0 to 100 reliability score. Receiving leads and associates can ask questions in plain English on a handheld ("Which vendors are likely to be late this afternoon?"). Every answer shows its evidence and a confidence level. The copilot also reads vendor emails and dock notes and proposes schedule changes that the receiving lead confirms. It is the same product for every chain: configured, never custom-coded.

## Why AI

A dashboard can list past deliveries; it cannot estimate what will happen this afternoon. Agreed delivery windows (the rule-based option) do not hold for NEX vendors. In our simulated test, the agreed window placed only 49% of arrivals within 45 minutes; a simple vendor average reached 63% and the ML model 70%. 55% of High-risk deliveries were actually late or rescheduled versus 11% of Low-risk ones. The LLM answers questions and reads vendor messages, but never calculates a prediction or score.

## Business model

- **Price:** \$99 per store per month on an annual contract; a \$25K paid pilot for up to 10 stores, credited to year 1. We pay for the AI; it is built into the price.

- **Customer return:** a store pays \$1,188 a year and saves about \$5,100 (4.3x). In a stress test with cheaper labor and lower impact it still saves \$2,700 (2.3x).

- **Our economics:** \$14 per store per month to serve (86% gross margin); break-even at about 1,500 stores live in year 3; about \$1.1M profit in year 4 on 3,000 stores (6.6% of US supermarkets).

- **The ask:** a \$1.5M seed round, which covers about \$1.0M of losses to break-even with a \$500K buffer.

## Recommendation: Pilot

Fund the seed round and run a **10-week paid pilot with one chain** on real NEX delivery data. The pilot decides what happens next:

- **Success** (≥80% of arrivals within ±45 min and ≥40% of late or no-show deliveries planned for in advance): roll out across the chain and sign the second chain.

- **Conditional** (70-80% accuracy or 25-40% planned for in advance): add weather and traffic signals, run a second pilot, consider outcome-based pricing.

- **Fail** (not better than a simple vendor average): stop, with the loss capped at about \$250K.

All money figures are planning assumptions, documented in Appendix/Metrics/VendorPulse_Business_Model.xlsx.
