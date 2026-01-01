# 📊 Quality Engineering KPI Framework
> **Strategy:** Moving from "Activity-Based Metrics" (How much did we do?) to "Outcome-Based Metrics" (How much value did we add?).

---

## 🏗️ 1. Shift-Left / Requirement Phase
*Goal: Measure the prevention of defects before a single line of code is written.*

| KPI | Target | Why it matters to the Lead |
| :--- | :--- | :--- |
| **Requirement Ambiguity Rate** | < 10% | Measures the effectiveness of the [Three Amigos Checklist](../03-Operational-Delivery/THREE_AMIGOS_CHECKLIST.md). |
| **Defect Injection Rate** | Downward Trend | Tracks if quality is being "designed in" vs. "tested in." |

---

## 🤖 2. Automation Engineering Phase
*Goal: Measure the health and ROI of our 4 technical frameworks.*

| KPI | Target | Lead Action |
| :--- | :--- | :--- |
| **Automation Stability (Flakiness)** | > 98% Pass | Tests failing without bugs are quarantined per the [Pruning Policy](./AUTOMATION_ROI_MODEL.md). |
| **Feedback Loop Time** | < 10 Minutes | Ensuring [CI/CD Sharding](../01-Strategic-Governance/TECHNOLOGY_STACK.md) is scaling with the code. |
| **In-Sprint Automation %** | > 80% | Measures the gap between "Feature Ready" and "Automation Ready." |
| **Script Maintenance Ratio** | < 15% | Ensuring we aren't spending more time fixing tests than building them. |

---

## 🚀 3. Execution & Release Phase
*Goal: Measure the efficiency of the "Quality Gate."*

| KPI | Target | Strategic Insight |
| :--- | :--- | :--- |
| **Defect Detection Percentage (DDP)** | > 90% | What % of bugs did QA find vs. the customer? |
| **Test Execution Velocity** | Increasing | Measures the impact of [Gen AI Acceleration](./GEN_AI_TRANSFORMATION.md). |
| **Mean Time to Detect (MTTD)** | < 1 Hour | How fast does our automation catch a breaking change in the pipeline? |

---

## 🛡️ 4. Post-Release (Shift-Right)
*Goal: Measure the ultimate business impact and cost of quality.*

| KPI | Target | Executive Value |
| :--- | :--- | :--- |
| **Defect Leakage (Escaped Bugs)** | < 2% (P0/P1) | The primary metric for [Risk-Based Testing](../01-Strategic-Governance/RBT_PRIORITY_MATRIX.md) success. |
| **Mean Time to Repair (MTTR)** | < 4 Hours | Speed of recovery, supported by [AI-Driven RCA](../04-Business-Value-ROI/GEN_AI_TRANSFORMATION.md). |
| **Cost of Quality (CoQ)** | Decreasing YoY | Proving the [Automation ROI](./AUTOMATION_ROI_MODEL.md) is actually hitting the bottom line. |

---

## 🛠️ Implementation: The "Metrics that Matter" Dashboard
I advocate for a live dashboard (Allure, Grafana, or PowerBI) rather than manual reporting. 

> **Lead Narrative:** "I don't report on 'passed tests.' I report on **Risk Coverage** and **Release Confidence**. If our Defect Leakage is low and our Feedback Loop is fast, the Engineering team can move with total autonomy."