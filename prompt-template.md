# IDEAL PROMPT Template — AI Sales Agent

Use this template to write the system prompt for the AI Agent node. Fill in each section for your own product/business. Sections can be trimmed for simpler use cases, but keep 1–3 and 6 at minimum.

## 1. Identity
- Agent name:
- Business it represents:
- Personality/tone (e.g. friendly, concise, upbeat, professional):
- Language(s) it should respond in:

## 2. Context
- What is being sold / what service is offered:
- Key products or service tiers (short list, not a full catalog):
- Pricing rules the agent is allowed to state (if any):

## 3. Conversation Goals
- Primary goal (e.g. "collect phone number to hand off to sales"):
- Secondary goal (e.g. "answer product questions", "reduce comment-to-DM friction"):

## 4. Qualification Logic
- What makes a lead "qualified"? (e.g. phone number provided + interest confirmed)
- What information must be collected before escalation?
- What disqualifies a lead (e.g. wrong country, spam, price-only shoppers)?

## 5. Conversation Flow
- Opening message behavior:
- How to handle objections/price pushback:
- How to close (ask for phone number, book appointment, etc.):

## 6. Guardrails (hard rules)
- Things the agent must NEVER do (e.g. give medical diagnoses, promise discounts not on file, discuss competitors)
- What to do when it doesn't know an answer (e.g. "escalate to human, don't guess")
- Tone boundaries (no sarcasm, no political topics, etc.)

## 7. Escalation Rules
- When to stop the AI and hand off to a human:
- What trigger phrase/condition ends automation for that conversation:

## 8. Output Format
- Should replies be short (1-2 sentences) or longer?
- Any formatting rules (no markdown in DMs, no emojis, etc.):

## 9. CRM / Data Mapping
- Which fields get sent to AMO CRM / Google Sheets (name, phone, product interest, source):
- Pipeline/stage the lead should land in:

## 10. Notification Rules
- What triggers a Telegram notification to the sales team:
- What information should the notification include:

## 11. Examples
- 2-3 example exchanges showing ideal agent behavior (good opening, good qualification, good escalation).

---

**Tip:** Keep sections 4 and 6 as strict, unambiguous rules — this is what prevents the agent from "helpfully" giving out information it shouldn't (discounts, diagnoses, guarantees) just because a customer pushes for it.
