# Whispr Frontier Demo Story

## Demo Title

Failed SOL transfer support ticket resolved with Whispr Frontier.

## Customer Ticket

> I tried to send 0.42 SOL from my Phantom wallet to my exchange deposit address, but the exchange never received it. Phantom showed an error first, then I retried. Can you check what happened?
>
> Wallet: `7mKXv6Y2nQ9bJ4rP8tV3zEaL5cHsF1wRuDqP6nM2kT9`
>
> Transaction: `5tX9Qp2Lk8Nf3Vz6YbC4rAh7DsE1mWqPjR6uTnK5sGx8Hv2Bc9Za4Ld7Ef6Mp1Qr`

## Mock Transaction Data

- Network: Solana mainnet-beta
- Signature: `5tX9Qp2Lk8Nf3Vz6YbC4rAh7DsE1mWqPjR6uTnK5sGx8Hv2Bc9Za4Ld7Ef6Mp1Qr`
- Sender wallet: `7mKXv6Y2nQ9bJ4rP8tV3zEaL5cHsF1wRuDqP6nM2kT9`
- Intended recipient: `Exch9WQ4uYp3N8rDc6Aa2LkMz5FpT1vB7sHdQxR4nK2`
- Amount: `0.42 SOL`
- Fee: `0.000005 SOL`
- Timestamp: `2026-04-30 12:18 UTC`
- Status: Failed
- Error: `Blockhash not found`

## Solana Lookup Result

Whispr looks up the transaction signature and finds that the transaction reached the network but was not finalized. The Solana response shows a failed transaction with `Blockhash not found`, meaning the transaction used an expired recent blockhash before it could be processed.

Whispr then checks the sender wallet and sees a later successful transfer of `0.42 SOL` to the same exchange deposit address at `2026-04-30 12:21 UTC`, three minutes after the failed attempt.

## Matched SOP/Docs

Matched SOP: `SOL-TRANSFER-FAILED-BLOCKHASH`

Summary:
- If a Solana transaction fails with `Blockhash not found`, explain that the transaction expired before confirmation.
- Confirm no funds moved in the failed transaction.
- Check for a later successful retry before advising the customer to resend.
- If a retry succeeded, tell the customer to wait for the recipient platform to credit the deposit.
- Do not promise exchange credit timing; suggest contacting the exchange if the deposit remains missing.

## Internal Whispr Diagnosis

The first transfer did not move funds because the transaction failed before finalization. The customer retried shortly afterward, and the second transfer to the same exchange deposit address succeeded. The likely issue is exchange-side deposit indexing delay, not a missing Solana transfer.

Whispr should draft a response for human approval that explains the failed attempt, confirms the successful retry, and avoids making claims about the exchange's internal crediting process.

## Draft Customer-Facing Reply

Hi,

I checked the transaction you shared. That first transfer failed on Solana with `Blockhash not found`, which means it expired before it could be confirmed. No SOL moved in that failed attempt.

I also found a later successful transfer of `0.42 SOL` from your wallet to the same exchange deposit address a few minutes later. From the Solana side, the retry appears to have completed successfully.

If the exchange still has not credited the deposit, the next step is to share the successful transaction signature with the exchange support team so they can check their deposit processing. We cannot control the exchange's internal crediting time, but the on-chain retry looks successful.

## 2-Minute Demo Narration Script

1. "Here is a realistic Solana support ticket: a customer says their exchange deposit never arrived after a failed Phantom transfer."
2. "Whispr reads the ticket and extracts the wallet address, transaction signature, amount, and customer intent."
3. "It performs a Solana lookup and sees the first transaction failed with `Blockhash not found`, so no funds moved."
4. "Whispr also checks the wallet history and finds a later successful retry to the same exchange deposit address."
5. "Next, it retrieves the matching support SOP for expired Solana blockhash failures."
6. "Whispr produces an internal diagnosis for the support teammate: the failed transaction is harmless, the retry succeeded, and any remaining delay is likely exchange-side."
7. "Finally, Whispr drafts a customer-facing reply. A human support teammate reviews and approves it before anything is sent."

## Acceptance Criteria Checklist

- Realistic demo ticket: a failed Phantom SOL transfer to an exchange deposit address.
- Mocked realistic transaction data: includes wallet, transaction signature, recipient, amount, fee, timestamp, status, and error.
- Solana lookup shown: explains failed transaction lookup and wallet-history retry check.
- Matched SOP shown: `SOL-TRANSFER-FAILED-BLOCKHASH`.
- Internal diagnosis shown: identifies failed first attempt, successful retry, and likely exchange-side delay.
- Customer-facing reply shown: includes a clear draft response for human review.
- Under 2 minutes: narration script is seven short steps designed for a concise demo video.
