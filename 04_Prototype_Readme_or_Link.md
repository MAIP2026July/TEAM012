# VendorPulse AI: Prototype / MVP

**Team:** TEAM012 · V V S S N Padmaji Saladi (2025mb26046) · MBA ZG583

## Links
- **Live demo:** https://claude.ai/artifact/7Si4qbkxUE6fwvSwYqg6vv (set sharing so the instructor can open it)
- **Code:** `Prototype/` folder in this package (repository link: [add if you push it to GitHub])
- **Screenshots:** `Appendix/Screenshots_or_Video/`

## Prototype type
Web app (one HTML file, works on desktop and handheld screen sizes) plus a Python ML pipeline.
The language layer is **Wizard-of-Oz**: a simple intent router stands in for the LLM so the demo runs without an API key. All predictions come from real trained models.

## What it demonstrates
The receiving lead's morning planning loop for one pilot store (simulated):
1. **Today:** vendors expected today, sorted by predicted arrival, with predicted window, risk (High / Medium / Low), confidence and evidence.
2. **Not enough data:** a new vendor with fewer than 8 deliveries gets no prediction or score.
3. **Ask the copilot:** plain-English questions; each answer shows the tools called, the data used and a confidence level. Out-of-scope requests (POs, chargebacks) are refused.
4. **Vendor messages:** AI-read email, dock note and voicemail with the extracted change. A person confirms or rejects. Low-confidence items can only be escalated.
5. **Override:** the lead can override any prediction with a reason.
6. **Vendor scores:** 0-100 reliability score with its four components.
7. **Model evidence:** the model compared with the agreed-window rule and a simple vendor average.

### Demo script (3 minutes)
1. Today tab: point out 4 high-risk vendors and the grey "not enough data" vendor.
2. Click "Which vendors are likely to be late this afternoon?" then "Why is Westside Tamale high risk?" Show the evidence and tool trace.
3. Click "When is Fresh Field Microgreens coming?" The copilot will not guess.
4. Click "Should we charge back Bay City Pierogi?" The copilot refuses and names the owner.
5. Vendor messages: confirm the Kalamazoo Tortilla email; show the voicemail cannot be confirmed. Return to Today to see the human override on the card.
6. Model evidence: 49% → 63% → 70% within ±45 min; the target is 80%, so the recommendation is a pilot.

## How the solution works (simple view)

| Step | File | What it does |
|---|---|---|
| 1 | `Prototype/model/generate_data.py` | Creates 18 months of **simulated** deliveries for 25 fictional NEX vendors (weekday routes, holidays, winter, reliability profiles, two new vendors). |
| 2 | `Prototype/model/train_and_evaluate.py` | Builds features from each vendor's past only (no peeking at the future), trains 3 models, tests them on Jun-Nov 2026 against two baselines, calculates scores, exports `app_data.json`. |
| 3 | `Prototype/app/build_app.py` | Puts the data into `template.html` to make `vendorpulse.html`. |
| 4 | `Prototype/model/make_chart.py` | Draws the model-vs-baseline chart. |

**Models**
- Arrival time: gradient-boosted regressor. Predicted window = prediction ±45 minutes.
- Late risk and reschedule / no-show risk: logistic regression (as accurate as gradient boosting here and easier to explain).
- Risk band: High if P(late or reschedule) ≥ 35%, Medium ≥ 18%, else Low.
- Reliability score: transparent rule. 40% on-time + 25% reschedule + 20% no-show + 15% count variance (last 90 days, minimum 8 deliveries).

**Features used:** vendor's 90-day late and reschedule rates, same-weekday late and reschedule rates (last 8), recent and same-weekday median arrival offset, arrival spread, holiday week, winter, agreed window hour.

**Results (simulated test set, 884 deliveries):**
| | Agreed window | Vendor average | ML model |
|---|---|---|---|
| Arrivals within ±45 min | 49% | 63% | **70%** |
| Late risk ROC-AUC | - | 0.72 | **0.76** |
| Reschedule risk ROC-AUC | - | 0.64 | **0.71** |

High-risk deliveries were actually late or rescheduled 55% of the time; Low-risk ones 11%.

## How to run it
```bash
pip install pandas numpy scikit-learn matplotlib
cd Prototype/model
python generate_data.py
python train_and_evaluate.py
python make_chart.py
cd ../app
python build_app.py        # then open vendorpulse.html in a browser
```

## Production design (not built in the prototype)
Azure OpenAI with tool calling replaces the intent router. Tools: `get_schedule`, `predict_arrival`, `predict_risk`, `get_vendor_score`, `get_vendor_history`, `extract_schedule_change`. Rule: every number in an answer must come from a tool result. Models run in Azure ML with nightly batch scoring and weekly retraining.

## What it does not yet prove
- Accuracy on real retailer data (all data is simulated).
- Real LLM answer quality and hallucination rate.
- Performance on Zebra handhelds over store Wi-Fi, and integration with the receiving system.
- Whether receiving leads adopt and trust it in daily use.
