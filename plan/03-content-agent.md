# 03 — The Content Agent: an AI System That Manages Your Content

Build this on **n8n + Claude** (you already run both). It saves you hours each week and doubles as
your strongest portfolio piece: "the AI system that runs my marketing."

Design rule: **the agent drafts, schedules and analyzes — you approve.** Nothing gets published
without your approval, and the agent never posts comments or DMs as you automatically (that hurts
trust and breaks most platforms' terms).

---

## 1. Architecture

```
            ┌──────────────── Capture ────────────────┐
 Telegram / WhatsApp voice note, email, web clipper, GitHub commits, client wins
            └───────────────────┬─────────────────────┘
                                ▼
                    [1] Idea Inbox Agent
            transcribe → clean up → tag pillar/platform → score
                                ▼
                  Content DB (n8n Data Table / Airtable / Notion)
                                ▼
                    [2] Planner Agent  (weekly, Monday)
            builds the week's calendar from best ideas + pillar mix
                                ▼
                    [3] Writer Agent
       per-platform drafts in YOUR voice (style guide + best past posts)
                                ▼
                    [4] Repurposer Agent
   long video/transcript → shorts scripts, posts, thread, newsletter, carousel
                                ▼
              Human approval (Telegram buttons: ✅ Approve / ✏️ Edit / ❌ Drop)
                                ▼
                    [5] Publisher
     schedule & post (LinkedIn API, X API, YouTube, Buffer/Typefully/Metricool)
                                ▼
                    [6] Engagement Assistant
     collects comments/DMs → classifies (lead / question / spam) → drafts replies for you
                                ▼
                    [7] Analytics Agent  (weekly, Friday)
        pulls metrics → finds winners → report + suggestions → feeds back into [2]
```

---

## 2. The agents

| # | Agent | Trigger | Model | Job |
|---|---|---|---|---|
| 1 | **Idea Inbox** | Telegram message / email / webhook | Small fast model (Haiku) + Whisper for voice | Transcribe, summarize, tag pillar & platforms, score 1–10, dedupe, store |
| 2 | **Planner** | Schedule — Monday 08:00 | Strong model (Sonnet) | Pick 5–7 ideas, balance pillars, assign dates/platforms, send plan for approval |
| 3 | **Writer** | Planned item approved | Strong model (Sonnet/Opus) | Write drafts per platform using style guide, hook library, and top-performing past posts as examples |
| 4 | **Repurposer** | New YouTube video / long transcript | Strong model | Find 3–5 clip moments with timestamps, write shorts scripts, thread, newsletter section, carousel outline |
| 5 | **Publisher** | Approved + scheduled time | No LLM | Post via APIs or a scheduler; save post URL & ID back to DB |
| 6 | **Engagement Assistant** | Every 2h | Small model | Pull comments/DMs, flag leads, draft replies — **you send them** |
| 7 | **Analytics** | Schedule — Friday 16:00 | Strong model | Fetch metrics, compute per-pillar/format performance, write report, update "what works" notes |
| + | **Lead Router** (optional) | Lead flagged by #6 or form submit | Small model | Enrich lead, add to CRM, notify you, draft a personalized follow-up |

---

## 3. Data model (one table: `content_items`)

| Column | Type | Notes |
|---|---|---|
| id | string | |
| created_at | datetime | |
| source | enum | telegram, email, github, video, manual |
| raw_input | text | original note / transcript |
| idea_summary | text | |
| pillar | enum | demo, case_study, how_to, opinion, behind_scenes |
| platforms | list | linkedin, x, youtube, shorts, newsletter |
| score | number | 1–10 |
| status | enum | idea → planned → drafted → approved → scheduled → published → analyzed |
| scheduled_at | datetime | |
| draft_linkedin / draft_x / draft_script / draft_newsletter | text | |
| post_urls | json | per platform |
| metrics | json | impressions, likes, comments, shares, saves, clicks, followers gained |
| performance_score | number | normalized vs. your average |

Plus two reference docs the agents read every time:
- **`style-guide.md`** — your voice, words you use/avoid, audience, CTA rules, formatting per platform
- **`what-works.md`** — auto-updated by the Analytics Agent (best hooks, best times, best formats)

---

## 4. Tech stack

| Layer | Choice |
|---|---|
| Orchestration | **n8n** (one workflow per agent; shared error workflow → Telegram alert) |
| LLMs | Claude — Haiku for classification/tagging, Sonnet for writing/planning, Opus for hard strategy/reports |
| Speech-to-text | Whisper / Deepgram (voice notes, video transcripts) |
| Storage | n8n Data Tables to start → Supabase/Airtable/Notion when you want a UI |
| Approval UI | Telegram bot with inline buttons (fast on mobile) or Slack |
| Publishing | LinkedIn API (Community Mgmt), X API, YouTube Data API — or simpler: Buffer / Typefully / Metricool API |
| Analytics | Platform APIs or the scheduler's analytics API |
| Visuals (optional) | Canva API / templated carousels, auto-captions with Submagic/Opus Clip |

---

## 5. Build order (MVP in 2 weekends)

**v1 — Weekend 1 (core loop)**
1. Telegram bot → Idea Inbox Agent → save to Data Table
2. Writer Agent: on command `/draft <id>` produce LinkedIn + X drafts → send to Telegram with Approve/Edit buttons
3. On approve → push to Buffer/Typefully queue

**v2 — Weekend 2 (automation)**
4. Planner Agent (Monday schedule) + weekly plan approval
5. Repurposer Agent for YouTube transcripts
6. Analytics Agent (Friday report) writing to `what-works.md`

**v3 — Later**
7. Engagement Assistant + Lead Router into CRM
8. Newsletter auto-assembly (weekly digest of your best posts + a new intro)
9. Evals: score drafts against style guide before they reach you; track your edit rate (target < 20% edits)

---

## 6. Example prompts (starting points)

**Idea Inbox — classify**
```
You are the intake assistant for an AI-engineer freelancer's content system.
Given a raw note, return JSON:
{ "idea_summary": str (1–2 sentences),
  "pillar": "demo"|"case_study"|"how_to"|"opinion"|"behind_scenes",
  "platforms": [..],
  "score": 1-10 (audience = small-business owners & agencies buying AI automation;
                 higher if concrete, demonstrable, has numbers),
  "hook_ideas": [3 short hooks] }
Raw note: {{raw_input}}
```

**Writer — LinkedIn**
```
Write a LinkedIn post in my voice. Follow style-guide.md strictly.
Audience: {{niche}} owners and agency founders.
Structure: hook (≤ 12 words, no emojis in line 1) → short story or problem → 3–5 concrete
points or steps → one-sentence lesson → single CTA: {{cta}}.
Max 1,300 characters. Short lines. No hashtags spam (max 3). No invented numbers —
only use facts from the source material.
Examples of my best posts: {{top_posts}}
What currently works: {{what_works}}
Source idea: {{idea_summary}} / {{raw_input}}
Return 2 variants with different hooks.
```

**Analytics — weekly report**
```
Here are this week's posts with metrics and my 8-week averages.
1) Top 3 and bottom 3 posts and the likely reason (hook, format, topic, timing).
2) Which pillar/format/time to double down on next week.
3) Update the "what works" list (max 10 bullets, replace weaker bullets).
4) 5 new post ideas based on what performed.
Be specific; no generic advice.
```

---

## 7. Costs (rough, per month)

- LLM usage for ~30 posts + reports: **~$5–20**
- n8n: self-hosted VPS ~$5–10 or n8n Cloud plan
- Scheduler (Buffer/Typefully): $0–30
- Transcription: ~$1–5

## 8. Guardrails

- Human approval before anything public; no auto-replies or auto-DMs
- Agent never invents client names, numbers or results — facts must come from the source note
- Client info only with written permission; strip PII before sending to LLMs
- Keep API tokens in n8n credentials, never inside prompts or the DB
- Log every draft + your edits — the diff is the best data for improving the style guide

---

## 9. Turn it into a product

Once it works for you, this system is sellable:
- **Content agent setup** for coaches, consultants, agencies ($2–5k setup + $300–800/month)
- n8n template on the n8n marketplace / Gumroad as a lead magnet or paid template
- A YouTube series: "Building my AI content team" — 5 episodes = 5 weeks of content
