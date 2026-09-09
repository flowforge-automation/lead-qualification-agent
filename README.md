# Lead Qualification & Follow-Up Agent

An AI agent that reads inbound lead messages (from a contact form, email, or CRM export), scores each one against qualification criteria, decides what should happen next, and drafts a personalized follow-up response — automatically. Unlike a simple trigger-based automation ("new form submission → send template email"), this is a **multi-step agent**: it reasons over unstructured text, makes a judgment call, and produces a different *kind* of output depending on that judgment.

## The problem this solves

Most small businesses and agencies get leads through a contact form or inbox, and every one of them gets treated the same way — either a generic auto-reply, or a human manually reading and triaging each message. That means:

- Hot, ready-to-buy leads sit in the same queue as spam and tire-kickers.
- Follow-up speed (which correlates directly with close rate) depends on someone checking their inbox.
- Low-value or clearly-not-a-fit leads still eat up someone's time to read and respond to.

This agent automates the *judgment* step, not just the reply step.

## How it works

1. **Input** — a CSV (or, in a live deployment, a webhook from a form/CRM) of raw lead messages: name, email, company, and their free-text message. See `sample-leads.csv`.
2. **Score** — the agent evaluates each message against 5 weighted criteria and produces a 0–10 score:
   - Clarity of need (0–2)
   - Budget signal (0–3)
   - Urgency / timeline (0–2)
   - Decision-making authority (0–2)
   - Service fit (0–1)
3. **Decide** — based on the score, the lead is routed into one of four outcomes: **Hot Lead** (7+), **Nurture** (3–6), **Not a Fit** (<3), or **Spam/Vendor Pitch** (0, filtered separately).
4. **Act** — the agent generates a *matching* response for each outcome — a hot lead gets a same-week call request, a nurture lead gets a no-pressure resource instead of a pushy pitch, a not-a-fit lead gets a polite decline, and spam gets no reply at all.
5. **Report** — everything is written to a lead tracker (`lead-tracker-output.csv`) and summarized in a client-ready report (`lead-tracker-report.pdf` / `.docx`).

## Files in this project

| File | What it is |
|---|---|
| `sample-leads.csv` | 5 example inbound leads used to demonstrate the agent (1 hot, 1 nurture, 1 not-a-fit, 1 more hot, 1 spam) |
| `lead-tracker-output.csv` | The agent's scored output: score, status, next action, and reasoning for each lead |
| `follow-up-drafts.md` | The actual personalized follow-up email the agent drafted for each lead |
| `lead-tracker-report.pdf` / `.docx` | A polished, client-facing summary report of the run |
| `case-study.md` | A walkthrough of the reasoning behind the scoring logic and example outputs |

## Why this matters for automation clients

A lot of "automation" projects stop at simple triggers: if X happens, do Y. This project demonstrates the next step up — an agent that reads unstructured input, applies judgment based on defined criteria, and takes a *different* action depending on what it concludes. That's the same underlying pattern needed for things like support-ticket triage, CRM record enrichment, or document intake — read something messy, decide what it means, act accordingly.

## Stack

- LLM-based scoring and generation (Claude / GPT-class model)
- CSV / webhook input (easily adapted to a form provider, Gmail, or CRM like HubSpot/Airtable)
- Output to a tracker (CSV/Sheet) and a generated report

---
*Built by Athanasios Kyratzis — [flowforge-automation](https://github.com/flowforge-automation)*
