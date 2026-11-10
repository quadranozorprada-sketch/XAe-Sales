# XAEROVA Voice Sales Arena V2 — pricing & consultative-sales beta

A voice-first B2B sales roleplay app. The browser sends microphone audio over WebRTC to OpenAI Realtime and plays the prospect's spoken replies. This is not the previous text-chat simulator.

## What is included
- Live speech-to-speech roleplay (not browser speech synthesis / not a scripted text bot)
- French and English session settings
- Ivorian French vs neutral French voice-style instruction
- Industry, prospect personality and difficulty controls
- XAEROVA product knowledge and guardrails embedded server-side
- Live transcript captions when available
- Server-side API key; browser receives only a short-lived client secret

## Requirements
- Node.js 20+
- An OpenAI API key with Realtime API access and billing enabled
- A modern browser with microphone access

## Run locally
1. Unzip this folder.
2. Copy `.env.example` to `.env`.
3. Put your API key in `.env` as `OPENAI_API_KEY=...`.
4. In this folder run:
   ```bash
   npm install
   npm start
   ```
5. Open http://localhost:3000. Grant microphone permission and start a voice session.

Use `localhost` for local testing. Deployed microphone access requires HTTPS.

## Important beta limitations
- This is a single-company XAEROVA beta. It has no user accounts, tenant isolation, persistent transcripts, billing, admin editor, CRM integration or analytics backend yet.
- Session settings and knowledge are in `server.mjs`; edit the `company` object and `buildInstructions()` to adjust them.
- The current build is an integration-ready starter, but it has not been connected to your private OpenAI account or tested with your API key. Live voice will work only after you configure a valid key and run it in a supported browser.
- The product knowledge is intentionally conservative: no claim that ANAC approvals are already granted; no promise of BVLOS; no invented thermal/multispectral features; drone replacement is separate; internet is paid by the customer.
- Before exposing it publicly, add authentication, rate limiting, tenant-specific knowledge isolation, consent/privacy controls, retention policy, monitoring and server-side session limits.

## Architecture
Browser microphone/audio ↔ WebRTC ↔ OpenAI Realtime API. Express server mints short-lived Realtime client secrets and keeps the permanent API key off the browser.

## Official technical reference
- https://developers.openai.com/api/docs/guides/voice-webrtc
- https://developers.openai.com/api/reference/resources/realtime/subresources/client_secrets/methods/create


## V2 commercial training configuration
- Upfront installation/activation fee: 1,860,000 FCFA.
- Ongoing subscription: 200,000 FCFA/month, additional to the upfront fee.
- The roleplay prompt now includes hidden buyer motivations, discovery-led questioning, price/total-cost objections, a structured closing path and explicit evidence/contract guardrails.
- The roleplay remains voice-first. This V2 prompt does not yet create a persistent coaching dashboard or guaranteed transcript-based scorecard. Those require a separate post-session transcript capture, analysis endpoint and storage layer.

## Commercial risks to resolve before selling
1. Define exactly what the 200,000 FCFA subscription includes: software access, support, maintenance, dock swap, preventive/corrective work, reporting, mission limits and response targets.
2. Specify contract start date, minimum term, renewal, cancellation, suspension for non-payment, price changes and termination consequences.
3. Clarify who owns the dock and equipment, when title transfers, and what happens to hardware and data on termination.
4. Define exclusions: internet, power, site works, theft, deliberate damage, weather/accident, third-party drone damage and drone replacement.
5. Define service geography, response-time measurement, replacement-stock availability and limits on swap commitments.
6. Show total cost transparently: 4,260,000 FCFA over 12 months; 9,060,000 over 36 months; 13,860,000 over 60 months, assuming subscription starts immediately and excluding taxes, internet, drone replacement and extras.
7. Validate unit economics. At a rough 600 FCFA/USD planning assumption, a dock manufacturing cost below USD 2,000 is below about 1.2m FCFA; against 1.86m upfront, that leaves less than about 660,000 FCFA before installation, logistics, support, warranty, sales costs, tax and overhead. Confirm actual landed cost before setting margin.
8. Have local counsel/accounting validate tax/VAT, consumer/business contract, data protection, aviation compliance and accounting treatment.

The prospect must never be trained to conceal recurring fees or imply customers have no choice after installation. Retention should be earned through measurable value and fair contract terms.


## Advanced persuasion and coaching engine (V3)

V3 adds:
- Hidden buyer profiles with role, authority, champion status, influencers, financial approver, technical evaluator, procurement and end-user roles.
- Three objection families: internal/personal, third-party/stakeholder, and external/circumstantial. The prospect reveals clues gradually and may have a genuine rather than disguised objection.
- Adaptive ethical persuasion reactions: framing, reframing, value anchoring, cost of inaction, contrast, future pacing, evidence/social proof, calibrated questions and commitment progression.
- A buyer-role selector to vary the prospect's position in the buying committee.
- Live transcript capture from Realtime input transcription and prospect audio transcripts.
- A post-session coaching endpoint that analyses the captured transcript and produces a scorecard, objection map, stakeholder map, persuasion review, improved wording and practice priorities.
- Transcript export as a text file.

### Important limitations
- Transcript capture depends on the Realtime API returning input transcription and output audio transcript events. If the browser/session does not return these events, the report will say there is insufficient evidence; it must not invent a review.
- The transcript is held in the current browser session and is not saved to a server database. Refreshing or closing the page loses the in-memory transcript. Export it before leaving if you need a copy.
- No account system, team administration, long-term analytics, CRM integration, or multi-tenant storage is included.
- The coach uses the OpenAI Responses API model `gpt-4.1-mini`; API access and billing must be enabled for both Realtime and Responses.
- The commercial contract is still not fully defined. The monthly subscription scope, ownership, term, cancellation, renewal, tax treatment and service levels need written decisions before being promised to customers.
- Persuasion is designed to be consultative and transparent, not coercive. Do not use fabricated urgency, false social proof, hidden recurring costs or pressure tactics.

### Upgrade from V2
Extract V3 into a new folder. Create `.env` from `.env.example` and add your own API key locally. Do not upload, paste, screenshot or share the key. Run `npm install`, then `npm start`, and open `http://localhost:3000`. Stop any older server first with Ctrl+C. Keep the terminal open while using the app.


## V4 — final decision-maker + three-minute assessment
- The person speaking is always the final decision-maker. They may delegate technical validation and daily operation to staff, but retain the final go/no-go decision.
- The buyer is a business decision-maker, not a drone pilot or automation engineer. They need to understand the business outcome, investment, risk and operational responsibilities—not technical implementation details.
- Sessions automatically end after 3 minutes. The user can also end early.
- The coaching report separates the buyer's commercial decision (YES / NO / NEXT STEP / NOT READY) from the buyer's satisfaction score (1–10). A prospect can say no and still be satisfied with the quality of the meeting.
- The buyer-role selector now offers final-decision-maker profiles only.

- At 15 seconds remaining, the app asks the buyer to state a concise final verdict; at 3:00 it automatically ends the call and starts the coaching report.


## V4.1 — correct salesperson / prospect roles
- The user is always the XAEROVA salesperson and leads the meeting.
- The AI is always the prospective customer and final decision-maker.
- The prospect opens with a neutral greeting and waits for the salesperson to begin discovery.
- The prospect never asks the salesperson what concerns them or reverses the interview.
- The prospect answers from the buyer's perspective and may challenge the offer with relevant customer questions.


## V4.2 — two-tier pricing and early-stage commercial realism
- Same upfront installation/activation fee for both offers: 1,860,000 FCFA.
- XAEROVA Standard: 108,000 FCFA/month (basic/non-AI offer: drone, piloting and avatar/standard operational functions).
- XAEROVA AI: 224,000 FCFA/month (Standard plus the AI functionality package).
- The prospect is trained to compare the tiers, ask what AI functions justify the difference, and examine internet, electricity, staffing, maintenance, drone replacement and other exclusions without inventing costs.
- The prospect challenges the seller about signed customer contracts, deployments, references, testimonials, results and demonstration videos. The simulator must not fabricate proof. It treats a pilot as a possible way to establish evidence, not as proof that already exists.
- Pilot price, duration, coverage, deliverables and success criteria remain to be proposed and agreed; the simulator does not invent them.
- Coaching now evaluates commercial clarity against both tiers and evidence discipline around XAEROVA's early commercial stage.
