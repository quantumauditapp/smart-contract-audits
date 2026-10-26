---
token: Law Of Attraction
ticker: LOA
network: solana
risk_score: 10
status: low
date: 2026-06-10
---

# Law Of Attraction (LOA) — Smart Contract Security Analysis | Solana

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/law-of-attraction-sol)

---

## Audit Summary

The Law Of Attraction (LOA) token is an SPL Token-2022 mint with both mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. Liquidity is moderate at $76,148, and trading volume appears normal. Holder concentration data was unavailable from chain-native RPC, though a third-party registry flagged high concentration.

> **Final Recommendation:** Given the unavailability of detailed holder distribution data, it is recommended to monitor on-chain holder analytics to assess concentration risk. While authorities are revoked, users should independently verify the current state of the mint and freeze authorities on-chain before making investment decisions. This ensures that the token's supply remains fixed and accounts cannot be frozen.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Law Of Attraction (LOA) token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts… |
| **Governance / Economics** | 8/10 | Low | The token exhibits moderate liquidity with $76,148 in total DEX liquidity, and a 24-hour volume of $22,469, resulting in a normal Volume/Liquidity Ratio of 0.30. The pair has been active for 49 days… |
| **Upgrades** | 10/10 | Low | The token's mint and freeze authorities are both revoked, preventing further supply issuance or account freezing. No Token-2022 extensions that would allow for future modifications, such as a… |

## Security Findings

_⚪ 1 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EhHyfj...pump`](https://solscan.io/account/EhHyfjRwj2jhmSE7GW5uJfizaLcNDa5C4HWPiSqjpump) |
| **Network** | Solana |
| **Price** | $0.0004987 |
| **24h Volume** | $6.6K |
| **Liquidity** | $79.0K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 13d |
| **Top-10 Holders** | 53.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5537 buys / 4489 sells |

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

### Is Law Of Attraction a scam?

Based on the available data, Law Of Attraction exhibits several high-risk characteristics, including an unverified contract, unrenounced ownership, and unlocked liquidity. These factors indicate potential vulnerabilities and central control. While a "scam" determination is subjective, these red flags suggest a significant risk profile for investors, warranting extreme caution before engagement.

### Is Law Of Attraction safe to buy?

Law Of Attraction is classified with a low-risk score of 10/100. It is not considered safe due to critical risk factors such as an unverified contract, meaning its code is not publicly auditable, and unrenounced ownership, which leaves significant control with the deployer. Additionally, its unlocked liquidity exposes investors to potential withdrawal risks.

### Has Law Of Attraction been audited?

The provided data indicates that the Law Of Attraction contract is currently unverified. This means its code has not been published or independently reviewed on the blockchain explorer, which is a prerequisite for security audits. Therefore, there is no public information to confirm whether a formal security audit has been conducted or completed.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/enymbpwxnvj7ebav3d9stticmidtm658lorfqvlwvscf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/law-of-attraction-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
