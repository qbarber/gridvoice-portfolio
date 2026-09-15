# GridVoice Community

**AI-powered negotiation intelligence for communities facing data center development.**

Built by [Quentin Barber](https://www.linkedin.com/in/quentinbarber/) — product leader and technologist focused on tools that give underserved communities real leverage.

🌐 **Live tool:** [gridvoice.app](https://gridvoice.app)  
📬 **Contact:** quentin.barber@gmail.com  
🔒 **Source code:** Private — available to vetted collaborators and community partners on request

---

## The Problem

When a hyperscale data center wants to move into a community, the developer has lawyers, lobbyists, and years of negotiation experience. The community usually has a city council meeting and a Google search.

Data centers bring real tradeoffs — tax revenue and jobs, but also diesel generator emissions, water consumption, noise pollution, and rising electricity rates. Communities in high environmental justice burden areas bear the most risk and have the least power to negotiate.

GridVoice changes that.

---

## What It Does

GridVoice is a community impact analysis tool that turns public data into negotiating power. A community representative enters a ZIP code and proposed project size — GridVoice does the rest.

### Four analysis tabs:

**Air, Water & Health**  
Real-time air quality data (EPA AirNow), projected health cost impacts (CDC PLACES), and regional water stress analysis based on the proposed power source and facility size.

**EJ Burden**  
Environmental justice percentile score pulled from EPA EJScreen 2024 — 243,000+ block group records. Shows where this community sits relative to the rest of the country on cumulative pollution burden, demographic vulnerability, and health risk.

**Economic**  
Projected tax revenue, job creation, and net community economic impact — scaled to actual project MW size and local income data.

**Community Negotiation** *(the core feature)*  
AI-powered negotiation brief generated for this specific community. Pulls together the EJ score, health impacts, water stress, and economic data — runs it through a CBA research knowledge base — and produces:

- A leverage score (1–10) with plain-language explanation
- Top 3 prioritized demands with realistic dollar ranges
- An opening statement the community rep can use at the first negotiation meeting
- Red lines to watch for
- Comparable communities and what they achieved
- Interactive sliders pre-populated with AI-recommended floor/realistic/stretch ranges, updating net annual impact in real time

---

## Why This Matters

Data center development is accelerating across the US, and community opposition has grown with it — in Virginia, Arizona, Ohio, Georgia, and Indiana — over rising electricity bills, noise pollution, water consumption, and emissions from diesel backup generators.

Communities have leverage they often don't know how to use. A high environmental justice burden score, a zoning variance requirement, or an organized coalition can shift negotiations significantly. GridVoice makes that leverage visible and actionable.

---

## The Pivot

An earlier version of this tool ([GridVoiceMVP-APP](https://github.com/qbarber/GridVoiceMVP-APP)) tried to serve every stakeholder — developers, planners, utilities, and communities — with separate dashboards for each. It was technically functional and architecturally complete.

It was also the wrong product.

The communities with the most to gain are the ones least served by generic dashboards. Rebuilding with a single intentional audience — community representatives navigating their first data center negotiation — produced something meaningfully better. This is that rebuild.

---

## Technical Architecture

**Frontend:** React + Vite + Tailwind CSS  
**Backend:** Express (Node.js)  
**Database:** Supabase (PostgreSQL)  
**AI Layer:** Groq API + openai/gpt-oss-120b — free inference, no per-user charges  

**Data Pipeline:**
| Source | Data | Status |
|--------|------|--------|
| EPA EJScreen 2024 | Environmental justice burden (243K block groups) | ✅ Live |
| EPA AirNow API | Real-time air quality | ✅ Live |
| CDC PLACES API | Community health outcomes | ✅ Live |
| US Census Bureau | Demographics and income | ✅ Live |
| WRI Aqueduct | Regional water stress | ✅ Live |
| NREL Grid Data | Grid emissions factors | ⏳ Reconnecting |

**AI Pattern:** Retrieval-Augmented Generation (RAG) — community data is computed first, then passed with a structured CBA knowledge base into the LLM prompt. The model reasons over comparable cases rather than general knowledge. Output is constrained to a strict JSON schema for reliable structured rendering.

---

## Research Basis

The negotiation knowledge base and comparable case ranges are grounded in published CBA research:

- Good Jobs First, *"Community Benefit Agreements with Data Centers Can Help Mitigate Harms"* (2024) — [goodjobsfirst.org](https://goodjobsfirst.org/community-benefit-agreements-with-data-centers-can-help-mitigate-harms/)
- Good Jobs First, *"What to Ask When a Data Center Wants to Come to Town"* (2024) — [goodjobsfirst.org](https://goodjobsfirst.org/what-to-ask-when-a-data-center-wants-to-come-to-town/)
- Brookings Institution, *"Why Community Benefit Agreements Are Necessary for Data Centers"* (January 2026) — [brookings.edu](https://www.brookings.edu/articles/why-community-benefit-agreements-are-necessary-for-data-centers/)
- Partnership for Working Families / PowerSwitch Action — [forworkingfamilies.org](https://forworkingfamilies.org)
- EPA EJScreen 2024 — [epa.gov/ejscreen](https://www.epa.gov/ejscreen)

> **Disclaimer:** Negotiation ranges shown in the tool represent typical patterns from CBA research — not single verified agreements. Always consult a community attorney before formal negotiations.

---

## Project Status

- ✅ Phase 1 — Data pipeline, EJ burden, air/water/health analysis
- ✅ Phase 1.5 — AI negotiation coach, CBA knowledge base, community negotiation tab
- 🔲 Phase 2 — Verified CBA case database, PDF export, dynamic comparable matching
- 🔲 Phase 3 — Community partnerships, city-specific deployment

---

## Work With Us

GridVoice is being developed as both an open resource for communities and a potential consultancy for environmental justice organizations, city governments, and community coalitions navigating data center negotiations.

If you represent a community organization, city council, or EJ nonprofit — or if you're an employer or collaborator interested in the project — reach out directly.

📬 quentin.barber@gmail.com  
💼 [linkedin.com/in/quentinbarber](https://www.linkedin.com/in/quentinbarber/)  
🔒 Source code available to vetted partners on request

---

*GridVoice is not a law firm and does not provide legal advice. All analysis is based on public data and published research. Consult a qualified attorney before entering formal negotiations.*
