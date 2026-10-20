# 01 — Freelancer Roadmap: Automations & Private SaaS (12 months)

Goal: go from "I can build systems" to a freelance developer known for **business automations and
custom (private) SaaS** in a clear niche, with a portfolio that sells for you, a steady lead flow, and $10k+/month in recurring revenue.

---

## 0. Pick a positioning (week 1)

You build two things: **automations** (n8n + AI connecting the tools a business already uses) and
**private SaaS** (custom web apps built for one business: internal systems, client portals, dashboards).
That combination is your edge: most automation freelancers can't build an app, and most developers
don't think in business processes. Sell it as one result.

Use this formula:

> I help **[specific business type]** **[get a measurable result]** by building **custom software and automations** around how they actually work.

Examples:

| Niche | Offer | Why it sells |
|---|---|---|
| Construction / renovation / real estate developers | Private project-management system: projects, suppliers, quotes, budgets, client portal + automated reports & reminders | Run on Excel + WhatsApp today; money leaks in every project |
| Service businesses (clinics, agencies, contractors) | Custom CRM / booking / job-management app + automated follow-ups, invoices, reviews | Off-the-shelf tools don't fit; staff waste hours on admin |
| Small–mid companies with "Excel hell" | Replace spreadsheets with an internal web app + dashboards + data entry automation | Errors, no single source of truth, owner has no visibility |
| Businesses already on SaaS tools | n8n + AI glue between CRM, accounting, email, WhatsApp, Sheets | Quick wins, low risk, a good entry point to a bigger build |

**Recommendation:** pick **one** industry you understand (e.g. *construction & real-estate
companies*) as your main niche, and use automation projects as the low-risk entry offer that leads to
the bigger private-SaaS build. Being "the person who builds systems for construction companies" is far
more memorable than "full-stack + automation developer".

Deliverable for week 1: a one-sentence positioning, a 3-sentence bio, and a list of 50 target businesses.

---

## 1. Skills stack (ongoing, prioritized)

Learn in this order, always by building:

**Automation**
- **n8n** (self-hosted + cloud), webhooks, REST APIs, JSON, error workflows; Make/Zapier familiarity
- Integrations businesses use: Google Workspace, Microsoft 365, CRMs (HubSpot, Monday, Pipedrive),
  accounting/invoicing tools, WhatsApp Business API, email, Slack/Telegram
- AI inside automations: LLM APIs (Claude, OpenAI), structured output, document/invoice data extraction,
  classification, summaries, agents with human approval

**Private SaaS / custom apps**
- TypeScript, **Next.js** (or React + a backend), Tailwind + a component library (shadcn/ui)
- **Supabase/Postgres**: data modeling, auth, row-level security, storage, edge functions
- Roles & permissions, multi-user (and multi-tenant if you resell one app to several clients)
- Forms, tables, dashboards, PDF generation, file uploads, notifications
- Payments (Stripe) when the client charges their own customers
- Internal-tool shortcuts when speed matters: Retool / Appsmith / Softr / Glide

**Production (what separates you from hobbyists)**
- Hosting & deployment: Vercel, Railway/Render, a VPS with Docker; domains, SSL, environments (dev/prod)
- Backups, monitoring & error alerts (Sentry, uptime checks), logs
- Security: auth done right, secrets management, access control, data privacy (GDPR / local law)
- Git, code reviews, documentation so the client isn't locked in
- Use AI coding tools (Claude Code etc.) to ship 3–5× faster — that's your margin

**Business**
- Discovery calls, mapping a business process, scoping, writing proposals, pricing, contracts, invoicing

**Rule:** every skill you learn becomes (a) a portfolio project and (b) a piece of content (see file 02).

---

## 2. Portfolio — 3 flagship projects (weeks 2–8)

Clients don't read CVs; they watch demos. Build 3 projects that map directly to what you sell:

1. **Private SaaS demo for your niche** — e.g. a construction project-management app: projects, tasks,
   suppliers, quotes vs. actual budget, document storage, client portal, owner dashboard.
   Show: 2-minute walkthrough video, screenshots, data model diagram.
2. **Back-office automation (n8n + AI)** — invoices/quotes/documents arrive by email → AI extracts the data →
   accounting/CRM/Sheets updated → exceptions sent to Slack/Telegram/WhatsApp for approval → weekly summary report.
3. **Automation + app working together** — e.g. leads from website/WhatsApp → n8n qualifies and creates
   a record in the custom app → automatic follow-ups → dashboard shows pipeline & conversion.

For each project publish a **case study** (GitHub README + LinkedIn post + short video):
- Problem → Solution → Architecture → Stack → Results (hours saved per week, errors removed, money tracked, cost to run) → Demo link

Build reusable foundations as you go (auth, roles, dashboard layout, PDF export, n8n templates).
Your 5th project should take half the time of your 1st — that's how fixed-price work becomes profitable.

Once you have real clients, replace demos with real case studies (with permission) and testimonials.

---

## 3. Offers & pricing

Sell **packages**, not hours. Productized offers are easier to sell and to deliver.

| Offer | What's included | Price range (starting point) |
|---|---|---|
| **Process Audit** (entry offer) | 60–90 min session + written report: how they work today, top 5 automation/software opportunities with ROI estimates | $300–$1,000 (credit toward a build) |
| **Automation Package** | 1–3 automations (n8n + AI), 1–3 weeks | $1,500–$6,000 |
| **Private SaaS MVP** | Custom web app with core modules, users & roles, dashboard, 4–8 weeks | $8,000–$30,000 |
| **System Build** | Custom app + automations + integrations + data migration | $20,000–$60,000+ |
| **Care Plan (retainer)** | Hosting, backups, monitoring, fixes, small features, monthly report | $300–$3,000 / month |
| **Hourly (only for consulting / extra features)** | Advisory, change requests outside scope | $80–$200 / hour |

Notes:
- **Always attach a care plan** to every app and automation: they need hosting, updates and fixes. Retainers are how you reach stable income.
- Pass usage costs (hosting, AI, messaging APIs, third-party licenses) through at cost or with a small margin, billed separately.
- Write scope in **modules and user stories**; anything new is a change request. Scope creep is the #1 profit killer in custom software.
- Decide IP up front: client owns their app on final payment, you keep your reusable components/templates.
- **Productize later:** when you build the same system for 3 clients in one niche, turn it into a multi-tenant SaaS you sell per month.
- Raise prices every 3 clients until you start losing ~30% of proposals.

---

## 4. Client acquisition channels

Use several channels in parallel; measure which brings paying clients.

1. **Warm network (fastest first client):** message 30 people you know: "I now build custom systems
   and automations for [business type] — do you know anyone who struggles with Z?"
2. **Content (long-term engine):** LinkedIn + YouTube/short video (see file 02).
3. **Direct outreach:** 10–20 personalized messages/day to your niche list. Lead with a free
   2-minute **Loom audit** of their business ("I noticed you manage quotes in Excel and WhatsApp —
   here's a 2-minute demo of how that would look as one system with automatic follow-ups").
4. **Platforms:** Upwork (automation, web app & SaaS development categories), Contra, Toptal (later), Fiverr Pro for productized gigs.
   Use them for early reviews, not as your only source.
5. **Partnerships:** web agencies, marketing agencies, accountants, CRM consultants, IT MSPs — they have
   clients asking for automations and custom systems and no one to build them. Offer white-label or referral fees (10–20%).
6. **Communities:** n8n community, indie-hacker / SaaS builder communities, local business groups, meetups. Help first, sell second.

---

## 5. Sales process

1. **Lead** → booking link (Cal.com/Calendly) with 3 qualifying questions
2. **Discovery call (30 min):** map the current process step by step, tools used, volume, cost of the problem, decision maker, budget, timeline
3. **Proposal within 48h:** problem, solution, scope, timeline, price, what's *not* included, next step
4. **Contract + 50% deposit** (Stripe / PayPal / bank transfer)
5. **Kickoff:** access, credentials (shared via a password manager), success metrics agreed
6. **Build in milestones** with a demo each week
7. **Handover:** documentation, user training, Loom walkthroughs, admin access, backup plan
8. **Upsell Care Plan** + ask for testimonial and referral at peak satisfaction

Templates to create once and reuse: discovery script, proposal, contract (MSA + SOW), onboarding
checklist, handover doc, testimonial request.

---

## 6. Business setup (do it once)

- Register as a freelancer / business entity in your country; get an accountant early
- Separate business bank account; invoicing tool (Stripe, Wise, Invoice Ninja, Green Invoice in Israel)
- Contract with IP transfer on final payment (excluding your reusable components), liability cap, data-processing clause, change-request process
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
| **Months 10–12** | Raise prices, templatize delivery, turn your most-repeated system into a multi-tenant SaaS for your niche | $10k+/month, 4+ retainers, waitlist |

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
