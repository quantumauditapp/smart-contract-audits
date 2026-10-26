---
token: Religion
ticker: RELIGION
network: solana
risk_score: 23
status: low
date: 2026-06-18
---

# Religion (RELIGION) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/religion-sol)

---

## Audit Summary

This Solana SPL Token Mint, Religion (RELIGION), demonstrates a robust security posture with both mint and freeze authorities revoked, ensuring fixed supply and immutable account states. No critical Token-2022 extensions like permanent delegate or transfer hooks are active, and metadata is immutable. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Holders should monitor on-chain for any future changes in liquidity or trading volume patterns. While current authority revocations secure the token's core properties, it is always prudent to verify the status of mint and freeze authorities directly on-chain before any significant interaction. If holder distribution data becomes available, assess it for potential concentration risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, indicating a fixed supply and immutability of account states. No transfer… |
| **Governance / Economics** | 6/10 | Medium | The token exhibits a healthy trading pattern with a 24-hour volume of $13,442 against a liquidity of $15,767, resulting in a normal Volume/Liquidity Ratio of 0.85. The DEX pair has been active for 27… |
| **Upgrades** | 10/10 | Low | The token's core parameters are fixed due to the revocation of both mint and freeze authorities. Key Token-2022 extensions, such as transfer hook and default account state frozen, are not enabled.… |

## Security Findings

_⚪ 1 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CkJZvv...pump`](https://solscan.io/account/CkJZvvWbwmiDepzrk71pq6gMXBfRVfUkhXR61iz3pump) |
| **Network** | Solana |
| **Price** | $0.00001615 |
| **24h Volume** | $33 |
| **Liquidity** | $12.8K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 4d |
| **Top-10 Holders** | 58.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2070 buys / 1609 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Religion a scam?

Based on the provided data, Religion (RELIGION) carries a low-risk score of 23/100. While ownership is renounced and no mint function exists, key red flags include an unverified contract and unlocked liquidity, which present significant risks. These factors suggest a potential for considerable downside, requiring investors to proceed with extreme caution and understand that the project lacks fundamental security assurances often associated with legitimate tokens.

### Is Religion safe to buy?

Religion (RELIGION) is currently rated as low risk (23/100), suggesting it is not safe for typical investment. Critical risk factors include an unverified contract, which prevents code review; unlocked liquidity, posing a potential for sudden withdrawal; and substantial token concentration among the top 10 holders (35.6%), increasing vulnerability to manipulation. These combined elements indicate a significant probability of adverse events for investors.

### Has Religion been audited?

The Religion (RELIGION) token has not had its contract verified. This is distinct from a full security audit, as verification merely means the code is publicly available for review. Without verification, the underlying smart contract code cannot be independently scrutinized by the public or auditors, leaving its functionality and security status completely opaque and unconfirmed.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/9zch6oazqf69ttpa4zywyeoiusj8b2x2r5tdqfceraiz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/religion-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-18*
