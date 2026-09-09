# Case Study: Lead Qualification & Follow-Up Agent

## The scenario

A service business (agency, contractor, consultancy — the pattern generalizes) gets inbound leads through a contact form. Right now, every message lands in the same inbox and gets the same treatment: someone has to read it, decide if it's worth pursuing, and write a reply. That doesn't scale, and it means the best leads don't always get the fastest response.

## The agent's job

Given a raw lead message, the agent has to do four things a simple automation can't:

1. Understand what the person is actually asking for (unstructured text, not a form field).
2. Judge how qualified they are, using consistent criteria.
3. Choose a *different* course of action based on that judgment.
4. Write a response that actually fits the situation — not a generic template.

## The scoring model

Each lead is scored out of 10 across five weighted signals:

- **Clarity of need (0–2)** — do they know what they want, or are they still exploring?
- **Budget signal (0–3)** — did they mention a number, a range, or budget authority at all?
- **Urgency / timeline (0–2)** — is there a deadline, or are they "just looking"?
- **Decision authority (0–2)** — are they the owner/decision-maker, or someone without authority to buy (e.g., a student, a junior employee)?
- **Service fit (0–1)** — does the request match services actually offered?

Thresholds: **7+ = Hot Lead**, **3–6 = Nurture**, **below 3 = Not a Fit**. A sixth check runs first — is this even an inbound customer lead, or an outbound vendor pitch/spam message? — which routes straight to "no reply" regardless of score.

## Walking through the 5 example leads

**Sarah Mitchell (Bright Bakery Co.) — scored 9/10, Hot Lead.**
She named the exact deliverable (redesign + online ordering), gave a concrete budget range ($8–12k), stated urgency ("this month"), and she's clearly speaking with owner-level authority for a 3-location chain. The agent's response skips discovery-of-basics and goes straight to proposing specific call times this week — because everything needed to move fast is already on the table.

**James Okafor (Okafor Landscaping) — scored 3/10, Nurture.**
He has a real problem (invisible online) but doesn't know what he needs yet, gave no budget, and explicitly said he's not in a rush. The agent doesn't try to force a sales call here — a pushy response to a "just exploring" lead usually backfires. Instead it drafts a low-pressure, resource-first reply that keeps the door open without wasting a sales cycle on someone who isn't ready.

**Priya Anand (student) — scored 1/10, Not a Fit.**
This reads like a lead (someone wants something from us) but it's an academic interview request with no budget and no commercial intent. The agent still responds politely rather than ignoring it — protecting reputation costs nothing — but correctly keeps it out of the sales pipeline.

**David Chen (Meridian Logistics) — scored 9/10, Hot Lead.**
Similar profile to Sarah: named deliverable (dashboard + workflow automation), strong budget ($15k+), confirmed authority (ops manager with budget sign-off), and a hard deadline (Friday, for a leadership meeting). The agent's draft response matches that urgency — proposing a call *tomorrow*, not "sometime this week."

**Marketing Solutions LLC — scored 0/10, Spam/Vendor Pitch.**
This message isn't a lead at all — it's someone else pitching *their* services to us. The agent correctly identifies the direction of the pitch is backwards and generates no reply, flagging it for archive instead. This is the kind of noise that otherwise clutters a shared inbox and wastes a human's triage time on every single run.

## Why the "different action per outcome" part matters

The easy version of this project would be: score the lead, then always send the same "thanks, we'll be in touch" template. That's barely more useful than not scoring at all. The harder — and more valuable — part is that a Hot Lead gets a same-week call request, a Nurture lead gets something low-pressure, a Not-a-Fit lead gets a short polite decline, and Spam gets nothing. Four different judgment calls, four different actions, from the same pipeline. That's the difference between a trigger ("new form submission → autoresponder") and an agent (read → decide → act appropriately).

## Where this generalizes

The same score → decide → act pattern applies directly to:

- Support ticket triage (urgent bug vs. feature request vs. spam)
- CRM record enrichment and prioritization
- Document/application intake (complete vs. missing-info vs. ineligible)
- Sales pipeline hygiene (flagging stale or unqualified deals for cleanup)

This project is deliberately built as a small, reviewable example of that pattern rather than a one-off script — the scoring criteria, thresholds, and response logic are all things a client can see, adjust, and trust before wiring it into their real inbox.
