# RippleRx — Care Coordination Dashboard

**A clinician-facing prototype that turns smart-dispenser signals into timely, personalized nudges — and shows, live, how those nudges move a patient's adherence risk.**

---

## 🎯 Elevator pitch

Medication non-adherence quietly drives a huge share of preventable hospitalizations — patients don't take their meds on time, care teams find out weeks later, and by then the damage (a stroke, a missed TB course, a cardiac event) is already done.

**RippleRx closes that loop.** It pulls signals from smart pill dispensers and turns them into a single, prioritized worklist for care coordinators — ranked by clinical risk, not just alphabetically. From there, a coordinator can send a clinician-reviewed reminder — complete with condition-specific diet and activity guidance — directly to the patient's phone in one click. The prototype simulates what happens next: when a patient responds to a reminder on time, their risk score visibly drops; when a dose is missed, it climbs. That feedback loop is the whole point — it's the difference between a dashboard that just *displays* risk and one that shows *how to reduce it*.

## 🩺 The problem

- Care teams are drowning in patient panels with no way to tell who needs attention **today**.
- Device data (a dispenser opening) gets treated as a binary "adherent/non-adherent" flag, losing all clinical nuance.
- Patient reminders, when they happen at all, are generic — "take your medication" — with no tailored lifestyle guidance and no way to see whether they actually helped.

## 💡 The solution

RippleRx is a single-pane command center that:

1. **Ranks patients by a multi-signal risk score** (device adherence, refill cadence, appointment attendance, activity trend) instead of a flat list.
2. **Surfaces the "why"** behind each risk score — pattern type, confidence level, and specific device/appointment/refill signals — so a coordinator isn't guessing.
3. **Sends a personalized, clinician-approved reminder** in one flow, with condition-specific dietary and physical-activity guidance (e.g., DASH-style tips for hypertension, post-meal walks for diabetes, cardiac-rehab-safe activity for post-MI patients) bundled in alongside appointment and dispenser reminders.
4. **Simulates the outcome** — a patient who receives and "acts on" a reminder sees their risk score drop, their adherence streak grow, and the change logged to a live timeline and trend sparkline. A patient with a missed dose sees the opposite. A one-click "Advance simulated day" shows the whole panel evolves at once.

## ✨ Key features

| Area | What it does |
|---|---|
| **Prioritized patient panel** | Auto-sorted by risk score, searchable by name or condition |
| **Risk detail view** | Device adherence, refill signal, appointment history, activity trend, and a live risk-trend sparkline |
| **Smart dispenser card** | Shows dose timing, on-time/late status, and current adherence streak |
| **Reminder builder** | Auto-drafted, editable patient message with a live phone preview; toggle appointment link, dietary guidance, activity guidance, and dispenser reminder independently |
| **Condition-aware recommendations** | Diet and activity tips generated per condition (hypertension, diabetes, post-MI cardiac, TB/DOTS), shown both in the care plan and in the patient's simulated phone view |
| **Working risk simulation** | Sending a reminder "now" measurably lowers risk; a "simulate missed dose" action raises it; "advance simulated day" resolves scheduled reminders and drifts unaddressed high-risk patients — demonstrating the intervention loop end to end |
| **Live, accurate counts** | Sidebar "needs review / late dose / on track" counts and the top alert banner are computed from real patient state, not hardcoded |
| **Accessibility built in** | Keyboard-navigable patient list, focus-trapped modal (Escape to close, focus returns to the trigger), skip-to-content link, high-contrast risk labels, screen-reader labels on every control, and a one-click larger-text mode |

## 🖥️ How to run it

It's a single self-contained HTML file — no build step, no server, no dependencies.

1. Download `RippleRx-Care-Dashboard.html`.
2. Open it in any modern browser (Chrome, Edge, Firefox, Safari).
3. Click a patient, click **Open reminder window**, adjust the toggles, and hit **Approve & send** to watch the risk score respond.
4. Use **Advance simulated day** to fast-forward the whole panel.

## 🗺️ Suggested demo script (for judges)

1. Open on **Suresh Pillai** (highest risk, late dose) — point out the alert banner and the "why" triggers.
2. Open the reminder window, show the auto-drafted message and phone preview updating live as you toggle diet/activity/appointment/dispenser options.
3. Hit **Approve & send** — risk score visibly drops, streak increments, timeline logs the event, sparkline updates.
4. Click **Simulate missed dose** on a different patient to show the panel can also flag deterioration.
5. Hit **Advance simulated day** to show the whole panel moves at once — this is the "system that closes the loop" moment.
6. Toggle **Aa** (larger text) and tab through the reminder modal with the keyboard to show accessibility wasn't an afterthought.

## ⚠️ Important disclaimers (keep these in any pitch)

- **This is a synthetic-data prototype**, not a validated clinical tool. All patients, conditions, and scores are fictional.
- Device events indicate medication was *removed* from the dispenser, not that it was *ingested* — this distinction is preserved throughout the UI intentionally.
- Diet and activity content is **generic, placeholder patient education**, explicitly marked as requiring clinician approval before ever reaching a real patient — RippleRx is a coordination and workflow tool, not a source of medical advice.
- The "risk decreases when reminded" logic is a **simplified simulation** built for demo purposes; a production version would need real adherence outcome data and clinical validation before any score could be trusted.

## 🛠️ Tech

Plain HTML/CSS/JavaScript, single file, zero dependencies — built this way deliberately so it's trivial to open, fork, or embed anywhere during a hackathon.

## 🚀 Where this could go next

- Real integration with dispenser APIs / FHIR adherence data instead of mock data
- Configurable risk-scoring weights per care team
- Two-way SMS/app acknowledgment instead of simulated outcomes
- Multi-language patient messaging
- Care-team assignment and audit trail for sent reminders
