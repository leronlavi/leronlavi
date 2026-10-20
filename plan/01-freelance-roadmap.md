# 01 — AI Engineer Freelancer Roadmap (12 months)

Goal: go from "I can build AI things" to a freelance AI engineer with a clear niche,
a portfolio that sells for you, a steady lead flow, and $10k+/month in recurring revenue.

---

## 0. Pick a positioning (week 1)

"AI engineer" is too broad to sell. Clients buy **a result for a type of business**.
Use this formula:

> I help **[specific business type]** **[get a measurable result]** with **[AI systems you build]**.

Examples that fit the stack you already use (n8n, voice agents, LLM APIs):

| Niche | Offer | Why it sells |
|---|---|---|
| Home services / construction / real estate | AI voice receptionist that answers calls 24/7, qualifies leads, books estimates | Missed calls = lost jobs. ROI is obvious. |
| Clinics, vets, dental | Voice + SMS booking agent, reminders, FAQ | High call volume, staff shortage |
| Agencies & small teams | n8n + LLM automations (lead intake, CRM, reporting) | They feel the pain of manual ops daily |
| B2B SaaS | RAG support bot / internal knowledge agent | Support cost reduction |

**Recommendation:** start with **one** primary niche (e.g. *AI voice agents + automation for home-service
businesses*) and one secondary "generalist" offer (custom n8n/LLM automations). You can widen later;
you can't be memorable while being generic.

Deliverable for week 1: a one-sentence positioning, a 3-sentence bio, and a list of 50 target businesses.

---

## 1. Skills stack (ongoing, prioritized)

You don't need a PhD. You need to ship reliable LLM systems. Learn in this order, always by building:

**Core (must have)**
- Python + TypeScript basics, REST APIs, webhooks, JSON
- LLM APIs (Claude, OpenAI): prompting, tool use / function calling, structured output, streaming
- Prompt caching, token cost control, model selection (big model for reasoning, small model for classification)
- Automation platforms: **n8n** (self-hosted + cloud), Make/Zapier familiarity
- RAG: chunking, embeddings, vector DBs (pgvector, Pinecone, Qdrant), hybrid search, reranking
- Agents: tool loops, MCP servers, memory, guardrails, human-in-the-loop approval
- Voice: Vapi / Retell / ElevenLabs, telephony (Twilio), latency tuning, call transcripts → CRM

**Production (what separates you from hobbyists)**
- Evals: test sets, LLM-as-judge, regression testing for prompts
- Observability: logging traces (Langfuse/LangSmith/Helicone), error alerts
- Deployment: Docker, a VPS or Railway/Render/Fly, Supabase/Postgres, env/secret management
- Security & privacy: PII handling, prompt-injection defenses, data retention, client data agreements

**Business**
- Discovery calls, scoping, writing proposals, pricing, contracts, invoicing

**Rule:** every skill you learn becomes (a) a portfolio project and (b) a piece of content (see file 02).

---

## 2. Portfolio — 3 flagship projects (weeks 2–8)

Clients don't read CVs; they watch demos. Build 3 projects that map directly to what you sell:

1. **AI Voice Receptionist demo** — calls a real number, answers FAQs, qualifies the caller,
   books into Google Calendar, logs to a CRM/Sheet, sends SMS/email summary.
   Show: 60-second screen+audio recording, architecture diagram, results metrics.
2. **Lead-to-CRM automation (n8n + LLM)** — web form/email/WhatsApp inbound → LLM classifies & enriches →
   CRM → personalized reply draft → Slack/Telegram alert.
3. **RAG knowledge agent** — chat over a company's docs/website with citations and evals.

For each project publish a **case study** (GitHub README + LinkedIn post + short video):
- Problem → Solution → Architecture → Stack → Results (time saved, calls answered, cost per run) → Demo link

Once you have real clients, replace demos with real case studies (with permission) and testimonials.

---

## 3. Offers & pricing

Sell **packages**, not hours. Productized offers are easier to sell and to deliver.

| Offer | What's included | Price range (starting point) |
|---|---|---|
| **AI Audit** (entry offer) | 60–90 min call + written report: top 5 automation opportunities with ROI estimates | $300–$1,000 (credit toward a build) |
| **Starter Build** | One automation or one voice agent, 2–3 weeks, 1 integration set | $2,500–$6,000 |
| **Pro Build** | Multi-agent system / RAG / voice + CRM + reporting | $7,500–$25,000 |
| **Care Plan (retainer)** | Monitoring, prompt tuning, fixes, monthly report, small changes | $500–$3,000 / month |
| **Hourly (only for consulting)** | Advisory calls | $100–$200 / hour |

Notes:
- Always attach a retainer to builds — AI systems need ongoing tuning. Retainers are how you reach stable income.
- Pass usage costs (LLM, telephony, hosting) through at cost or with a small margin, billed separately.
- Raise prices every 3 clients until you start losing ~30% of proposals.

---

## 4. Client acquisition channels

Use several channels in parallel; measure which brings paying clients.

1. **Warm network (fastest first client):** message 30 people you know: "I'm now building AI agents
   that do X for Y — do you know anyone who struggles with Z?"
2. **Content (long-term engine):** LinkedIn + YouTube/short video (see file 02).
3. **Direct outreach:** 10–20 personalized messages/day to your niche list. Lead with a free
   2-minute **Loom audit** of their business ("I called your office after hours and nobody answered —
   here's a demo of an agent that would have booked that job").
4. **Platforms:** Upwork (AI/automation category), Contra, Toptal (later), Fiverr Pro for productized gigs.
   Use them for early reviews, not as your only source.
5. **Partnerships:** web agencies, marketing agencies, CRM consultants, IT MSPs — they have clients
   asking for AI and no one to build it. Offer white-label or referral fees (10–20%).
6. **Communities:** n8n community, Vapi/voice AI Discords, local business groups, meetups. Help first, sell second.

---

## 5. Sales process

1. **Lead** → booking link (Cal.com/Calendly) with 3 qualifying questions
2. **Discovery call (30 min):** current process, volume, cost of the problem, decision maker, budget, timeline
3. **Proposal within 48h:** problem, solution, scope, timeline, price, what's *not* included, next step
4. **Contract + 50% deposit** (Stripe / PayPal / bank transfer)
5. **Kickoff:** access, credentials (shared via a password manager), success metrics agreed
6. **Build in milestones** with a demo each week
7. **Handover:** documentation, Loom walkthrough, training
8. **Upsell Care Plan** + ask for testimonial and referral at peak satisfaction

Templates to create once and reuse: discovery script, proposal, contract (MSA + SOW), onboarding
checklist, handover doc, testimonial request.

---

## 6. Business setup (do it once)

- Register as a freelancer / business entity in your country; get an accountant early
- Separate business bank account; invoicing tool (Stripe, Wise, Invoice Ninja, Green Invoice in Israel)
- Contract with IP transfer on final payment, liability cap, data-processing clause
- Professional email on your own domain, a simple website (landing page + case studies + booking link)
- Tool accounts in **your** name used for demos; client systems in **client** accounts

---

## 7. 12-month timeline

| Period | Focus | Targets |
|---|---|---|
| **Month 1** | Positioning, website, LinkedIn/GitHub profile, project #1 | Niche defined, 1 demo live, posting 3×/week |
| **Month 2** | Projects #2–3, outreach system, content agent v1 | 3 demos, 100 outreach messages, first discovery calls |
| **Month 3** | First paying clients (even at lower prices) | 1–2 clients, 1 testimonial, first case study |
| **Months 4–6** | Productize offers, raise prices, add retainers | $3–6k/month, 2+ retainers, 1 agency partnership |
| **Months 7–9** | Scale content (YouTube, newsletter), referrals | $6–10k/month, inbound > outbound |
| **Months 10–12** | Raise prices, subcontract/templatize delivery, consider a micro-product | $10k+/month, 4+ retainers, waitlist |

---

## 8. Weekly operating rhythm

| Day | Block |
|---|---|
| Mon | Plan week, review metrics, batch-record content (2h) |
| Tue–Thu | Client delivery (mornings), outreach + calls (afternoons) |
| Fri | Learning/building portfolio (half day), publish case study/long post, invoices |
| Daily | 30 min engagement on social, 10–20 outreach messages |

**Track weekly:** posts published, outreach sent, replies, calls booked, proposals sent, won/lost,
revenue, MRR from retainers.
