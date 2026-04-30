# Whispr Frontier MVP Scope

## Product One-Liner

Whispr Frontier is a human-in-the-loop AI support agent for Solana and Web3 support tickets that investigates issues, gathers relevant context, and drafts replies for a human reviewer to approve.

## MVP Flow

1. A support ticket is submitted with a user question, wallet address, transaction signature, error message, or other Web3 context.
2. Whispr Frontier classifies the ticket and identifies what information is needed to investigate it.
3. The agent checks relevant Solana/Web3 data sources, such as transaction status, wallet activity, program interactions, and known support knowledge.
4. The agent summarizes the likely issue, cites the context it used, and drafts a support response.
5. A human support teammate reviews the investigation and draft, edits if needed, and sends the final reply.

## Human-In-The-Loop Positioning

Whispr Frontier is not a fully autonomous support bot. It does not send responses directly to users, take account actions, or make irreversible decisions without review.

The MVP is designed to reduce support investigation time by preparing a clear draft and evidence summary while keeping final judgment and communication with a human operator.

## Solana/Web3 Integration

For the hackathon MVP, Solana integration focuses on support investigation rather than transaction execution. The agent can use Solana-specific context such as wallet addresses, transaction signatures, explorer links, token transfers, failed transactions, and program interaction history to help explain what likely happened.

The Web3 support angle includes common cases such as failed swaps, missing token balances, transaction confirmation questions, wallet connection issues, and user confusion around on-chain activity.

## Out Of Scope

- Desktop OCR overlays or screen-reading assistants.
- Fully autonomous support replies sent without human approval.
- Custodial wallet access, private key handling, or signing transactions.
- Automated refunds, account recovery, bans, escalations, or other irreversible actions.
- Broad CRM replacement features beyond the minimum ticket investigation and draft workflow.
- Production-grade fraud detection, compliance review, or risk scoring.
- Support for every blockchain ecosystem; the MVP is centered on Solana/Web3 support scenarios.

