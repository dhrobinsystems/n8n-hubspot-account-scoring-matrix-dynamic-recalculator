# ⚠️ Disclaimer & Liability Limitation

**Use at your own risk.** The code, workflows and scripts in this repository (`n8n-hubspot-account-scoring-matrix-dynamic-recalculator`) are provided for educational and architectural demonstration purposes.

## No Liability

The author and dhRobin Systems accept no responsibility or liability for any direct, indirect, incidental, or consequential damages that result from using, misusing, or deploying these scripts. This includes, without limitation:

- incorrect, incomplete or outdated ICP fit scores, account tiers or score-drift calculations;
- account tier upgrades or downgrades and any downstream territory assignment, owner routing, lead allocation, sequencing, advertising audience or compensation effects they trigger;
- overwritten, lost or corrupted HubSpot company properties, property history or reporting;
- decisions made from Slack alerts, audit records or other outputs of this workflow;
- API rate-limit violations, account suspensions, overage charges or service interruptions at HubSpot, Slack or any other connected provider.

## No Warranty

All software, n8n JSON blueprints, JavaScript modules, scoring matrices, default weights, tier thresholds and sample payloads are provided **"AS IS"**, without warranty of any kind, express or implied. This includes, but is not limited to, warranties of merchantability, fitness for a particular purpose, and non-infringement.

The default scoring weights, funding-stage points, technographic matrix and tier thresholds are **illustrative examples**. They are not validated against any real customer base. They do not predict revenue, conversion or deal outcomes, and they must be calibrated against your own historical data before use.

## Predictive Scoring & Tier Recalibration

- Composite scores are a deterministic weighted heuristic built from third-party signals (headcount, funding, technographics, firmographics). They are not a statistical forecast, and they are only as accurate as the data supplied.
- Weekly recalibration can move accounts between tiers because of data errors, enrichment-provider changes or timing artefacts, as well as genuine market change. Hysteresis and circuit breakers reduce this risk but do not remove it.
- Treat every computed score and tier as a **recommendation that a person must review** before it drives routing, outreach, prioritization or any decision affecting people or contracts.

## CRM Data Enrichment

- You are responsible for confirming that every enrichment source (headcount, funding events, technology-stack data) is licensed for storage in your CRM and for automated processing and scoring.
- Enrichment data may be inaccurate, stale or attributed to the wrong company. Validate the matching logic (domain, company ID) before you trust any signal.
- This workflow writes to HubSpot only when `SANDBOX_MODE=false`, `DRY_RUN=false` and `SCORE_UPDATE_ENABLED=true` are all set. Enabling those flags is your decision and your responsibility.

## Production Testing Required

Always test thoroughly in an isolated staging environment, such as a HubSpot developer test account or sandbox portal, with `SANDBOX_MODE=true` and `DRY_RUN=true` enabled, before you connect live HubSpot credentials, enable Slack alerts, or set `SCORE_UPDATE_ENABLED=true`. Review simulated batch payloads and audit records before you enable live writes, and spot-check updated records after the first live run.

## Third-Party APIs & Compliance

You alone are responsible for complying with the terms of service, rate limits, data privacy regulations (GDPR/CCPA), and security policies of HubSpot, Slack, your enrichment providers and any connected services. That includes:

- documenting how automated account scoring is used, and making sure it does not produce decisions with legal or similarly significant effects on individuals without meaningful human review;
- confirming a lawful basis for processing any personal data present in company records, execution history or alerts;
- keeping access tokens and webhook URLs in environment variables or a secrets manager, never in workflow JSON, source control or chat;
- configuring n8n execution-data retention and access controls to match your data-protection obligations;
- reviewing every automatically created or updated record.

## Sample Data

All sample data in this repository, including portal ID `99000001`, company IDs `44001`–`44005`, owner IDs, company names and `example.com` domains, is **synthetic and fictional**. Any resemblance to real organizations is coincidental.

---

Full text: DISCLAIMER.md · Licensed under the MIT License. License: MIT © 2026 DH Robin (dhRobin Systems) · Provided as-is, see the disclaimer.
