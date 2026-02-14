## Sample Questions :

1. Select a high-latency business process (e.g., insurance claims
processing or cargo scheduling). Identify three specialized agent roles that could handle
different sub-tasks. Draw a dependency graph showing which agents require data from
others and identify where a "balancing feedback loop" (like a human checkpoint) should
be placed.

Solution :
1) Three Specialized Agent Roles
Agent A — Intake & Document Validation

Purpose: Collect and verify claim submission
Tasks:

Receive claim form, photos, reports, invoices

Check completeness (missing docs, wrong formats)

Extract structured data (policy no, claim amount, incident date)

Send validated claim → downstream

Output → Clean, structured claim packet

Agent B — Assessment & Fraud Risk Analyzer

Purpose: Evaluate claim legitimacy and estimate loss
Tasks:

Cross-check policy coverage

Estimate claim value using rules/models

Detect fraud signals (duplicate claim, anomaly, suspicious patterns)

Assign Risk Score + Estimated Payout

Input: From Agent A
Output → {risk_score, payout_estimate, flags}

Agent C — Settlement & Payment Processor

Purpose: Final decision and payout execution
Tasks:

Approve / Reject / Escalate claim

Calculate final payable amount

Trigger payment

Notify customer

Input: From Agent B
Output → Settlement status + payment

        ┌──────────────────────┐
        │  Agent A             │
        │  Intake & Validation │
        └─────────┬────────────┘
                  │ structured claim
                  ▼
        ┌──────────────────────────┐
        │  Agent B                 │
        │  Assessment & Fraud      │
        └─────────┬────────────────┘
                  │ risk + payout
                  ▼
        ┌──────────────────────────┐
        │  Agent C                 │
        │  Settlement & Payment    │
        └──────────────────────────┘
