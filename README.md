# Instagram AI Sales Agent (n8n + SendPulse + GPT-4o-mini)

An open-source n8n workflow template that turns Instagram Direct Messages into a fully automated, AI-driven sales funnel — from first "hi" to a qualified lead in your CRM.

## Why this exists

Small and mid-size businesses running Instagram sales get flooded with DMs but can't afford a 24/7 human sales team. This workflow gives them an AI agent that:

- Talks to customers naturally in DM (via SendPulse's Instagram integration)
- Qualifies leads using a configurable conversation strategy
- Gates on collecting a phone number before treating a lead as "qualified"
- Pushes qualified leads into a CRM (AMO CRM) or a Google Sheet
- Notifies a Telegram group in real time when a hot lead appears
- Can run a second, silent "status-checker" agent in parallel to track conversation health without interrupting the sales flow

It's built from real automation work done for retail/e-commerce clients and generalized here so anyone can adapt it to their own business.

## Architecture

```
Instagram DM
   │
   ▼
SendPulse (OAuth, Instagram channel)
   │  webhook
   ▼
n8n Workflow
   ├── AI Agent node (GPT-4o-mini) — sales conversation + lead qualification
   ├── Conditional routing — has phone number? → mark as qualified
   ├── AMO CRM node — create/update lead
   ├── Google Sheets node — log every conversation (fallback / lightweight CRM)
   └── Telegram node — notify sales team of new qualified leads
```

## What's included

- `workflows/instagram-ai-sales-agent.json` — importable n8n workflow (sanitized, uses placeholder credentials)
- `docs/prompt-template.md` — the "IDEAL PROMPT" template used to configure the AI agent's persona, rules, and qualification logic

## Requirements

- [n8n](https://n8n.io) (self-hosted or n8n.cloud)
- A [SendPulse](https://sendpulse.com) account connected to an Instagram Business account
- An OpenAI API key (or any OpenAI-compatible endpoint) for the AI Agent node
- Optional: AMO CRM account and/or a Google Sheet for lead storage
- Optional: a Telegram bot + group for notifications

## Setup

1. Import `workflows/instagram-ai-sales-agent.json` into your n8n instance.
2. Connect your own credentials for SendPulse, OpenAI, AMO CRM / Google Sheets, and Telegram (all credential fields are placeholders — no real keys are included in this repo).
3. Customize the AI agent's system prompt using `docs/prompt-template.md` — adjust the product, tone, and qualification rules for your business.
4. Activate the workflow and connect the webhook URL inside your SendPulse Instagram bot flow.

## Customizing the AI agent

The prompt template is structured so you can define, section by section:

- Agent persona and tone
- Product/service knowledge
- Lead qualification rules (what counts as a "hot" lead)
- Escalation rules (when to hand off to a human)
- Guardrails (what the agent should never say or do)

This makes it straightforward to reuse the same skeleton for completely different products — sneakers, food delivery, clinic bookings, education — by only rewriting the prompt and swapping the CRM destination.

## License

MIT — use, modify, and redistribute freely. See `LICENSE`.

## Disclaimer

This is a generalized template extracted from client automation work. It contains no real client data, API keys, or business-identifying information. You are responsible for your own SendPulse/Instagram API usage complying with Meta's platform policies.
