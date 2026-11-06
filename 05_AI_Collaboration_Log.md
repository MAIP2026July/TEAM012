# AI Collaboration Log

**Team:** TEAM012 · V V S S N Padmaji Saladi (2025mb26046)

## Tools Used
- **Microsoft One Note:** for documentation and review
- **Claude (Anthropic):** drafting all documents, writing the prototype code (Python ML pipeline and web app), building diagrams and charts, and checking numbers.
- **Visual Studio Code:** to review the code and to update.

## Where AI Helped

| Area        | How AI helped                                                  |
| ----------- | -------------------------------------------------------------- |
| Drafting    | First draft of the Topic Approval Form by providing the real use case scenario from my organization                        |
| Wireframing | workflow and architecture diagrams; the working prototype screens serve as high-fidelity wireframes manually reviewed                      |
| Coding      | Prototype scaffolding and model code                           |
| Metrics     | proposed the metric tree, the go/no-go thresholds and the model-vs-baseline evaluation along with manual review               |
| Risk review | listed harm scenarios, controls and launch blockers     |

## Example Prompts or Workflows
The whole initiative followed one human-in-the-loop cycle: I set the problem and the constraints, AI built a draft, I reviewed it against my knowledge of the client's DSD process, AI fixed it, and I made the final call.

**Phase 1. Problem and scope (human-led)**
1. **Me:** Picked the Vendor DSD / NEX receiving problem from my organization's work with a retail supercenter client.
2. **Me:** Scoped the first wedge to vendor schedule, reliability score and delay / reschedule risk. POs, items, variances and vendor performance went to the roadmap.
3. **Me:** Wrote the Milestone 1 topic and strategy fix, kept the client anonymous, set the 80% arrival target, and submitted it.

**Phase 2. Plan the deliverables**

4. **Me > AI:** "Read the student packet and my Milestone 1 submission; list every required deliverable, format and folder."
5. **AI:** Listed the 10 deliverables, the folder structure, the 7 report sections and the recommendation options.
6. **Me:** Asked to create one document at a time to review and to suggest the changes accordingly, with only the important content in each document.
7. **AI:** Generated the 1st document
8. **Me:** Reviewed it, suggested the changes and repeated the flow

**Phase 3. Data and model**

9. **Me > AI:** "My client's data is confidential; simulate an NEX delivery history that mirrors the receiving patterns from my work."
10. **Me:** Asked to generate the sample vendors data related to retail stores
11. **AI:** Simulated 25 fictional vendors over 18 months
12. **Me:** Asked to generate a simple predictive ML model to predict vendors arrival, along with projecting calculated risks.
13. **AI:** Trained arrival, late-risk and reschedule-risk models against two baselines.
14. **Me:** Reviewed the first result. The model barely beat a simple average, so I rejected it.
15. **AI:** Added weekday-route behaviour, reran the models and made the model-vs-baseline comparison fair (same top 20% flagged).
16. **Me:** Checked the patterns against what I see in store receiving. Kept the 70% result, below the 80% target, and used the gap to recommend a pilot instead of tuning the data.

**Phase 4. Prototype and trust**

17. **Me > AI:** "Build a handheld-friendly copilot: today's schedule, risk, evidence, vendor scores, Q&A, with human control."
18. **AI:** Built the web app with confidence and evidence on every answer, overrides with a reason, and confirmation of changes read from vendor messages.
19. **AI + Me:** Testing found three issues: a new vendor still got a prediction, "charge back" bypassed a guardrail, and confidence shared the risk colour. AI fixed them; I re-checked.
20. **Me:** Set the trust rules: nothing from a vendor message changes the schedule without the receiving lead; vendor scores are hidden from dock associates; the minimum is 8 deliveries before any prediction or score.

**Phase 5. Documents and deck**

21. **Me > AI:** "Draft the executive summary, final report and appendix, using numbers taken directly from the evaluation output."
22. **AI:** Drafted the documents, diagrams and chart; every economics input was labelled as an assumption.
23. **Me:** Reviewed each document, replaced assumed inputs with near realtime figures based on my knowledge at client, and corrected wording.
24. **Me > AI:** "Build a presentation deck in the packet's order, with speaker notes."
25. **AI:** Built a 14-slide deck ending with the pilot recommendation.
26. **Me:** Rehearsed with the live prototype and adjusted the slides.

**Phase 6. Disclosure**

27. **Me > AI:** Give me the requests I made as a workflow between me and AI to record.
28. **Me:** Review and updated as appropriate

## Where AI Was Weak or Wrong
These were found while checking the work:
- **Weak first simulation:** the first data simulation had almost no learnable pattern, so the model barely beat a simple vendor average. A model that "wins" on meaningless data proves nothing, so the simulation was redesigned around realistic weekday-route behavior.
- **Unfair comparison:** the first high-risk comparison used different thresholds for model and baseline, which made the baseline look better on recall and the model better on precision. It was changed to flag the same 20% of deliveries for both.
- **Cold-start leak:** a recently onboarded vendor still received a prediction because the history cut-off was too generous. Corrected so vendors under 8 deliveries get "not enough data".
- **Guardrail gap:** the copilot refused "chargeback" but answered "charge back" (two words). Fixed and re-tested.
- **Confusing UI signal:** "High confidence" used the same red color as "High risk". Confidence now has its own neutral style.
- **Accuracy below target:** arrival accuracy is 70%, under the 80% target from Milestone 1. This was reported as-is rather than tuned upward, and it drives the "pilot, not scale" recommendation.
- **Generic outputs to watch:** AI-drafted economics use assumed figures (labor rate, wait time, LLM price per question). These are labeled as assumptions, not facts.

## Human Corrections

| What I changed | Why | Judgment applied |
| --- | --- | --- |
| Used a real use case from my organization (Vendor DSD / NEX receiving) instead of an AI-suggested idea | A problem I see daily makes a credible, grounded product story | Problem selection and domain expertise |
| Narrowed the MVP to vendor schedule, reliability score and delay / reschedule risk; moved POs, items, variances and vendor performance to the roadmap | A narrow wedge can be built and proven; that data is not reliable enough yet | Scope trade-off |
| Kept the client anonymous, used fictional vendor names and simulated data | Client data is confidential and cannot leave the organization | Professional integrity |
| Asked for one document at a time and reviewed each before the next | Catch errors early and keep only the important content | Quality control |
| Rejected the first model result | It barely beat a simple vendor average; a model that wins on patternless data proves nothing | Analytical rigor |
| Checked the simulated patterns against real store receiving | Simulated weekday-route behaviour had to match what happens at the dock | Domain validation |
| Kept the 70% arrival accuracy instead of tuning it to the 80% target; recommended Pilot, not Scale | Honest evidence matters more than a good-looking number | Decision-making under uncertainty |
| Required the receiving lead to confirm any schedule change read from a vendor message | A wrong automatic change leaves the dock unstaffed | Human-in-the-loop design |
| Hid vendor scores from dock associates | Vendor performance data is commercially sensitive | Privacy and governance |
| Set a minimum of 8 deliveries before any prediction or score | New, small vendors should not be judged on too little data | Ethics and fairness |
| Replaced assumed economics inputs with near-real-time figures from my client knowledge | AI used generic assumptions (labor rate, deliveries per week, wait time) | Business judgment |

## Final Reflection
- **Where AI accelerated PM work:** AI helped me to generate the required content so fast based on the context and guidelines provided. I worked through chain of thoughts to come up with a required output. Overall, it helped me to complete my final output.

- **Where AI could not replace PM reasoning:** getting the real workd process and its current challenges, getting the real data, judging whether the simulated patterns match real NEX vendor behavior, choosing what store users should and should not see, deciding the recommendation and the risk you are willing to accept.