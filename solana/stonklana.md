---
token: STONKLANA
ticker: STONKLANA
network: solana
risk_score: 9
status: low
date: 2026-10-28
---

# STONKLANA (STONKLANA) — Smart Contract Security Analysis | Solana

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stonklana-sol)

---

## Audit Summary

STONKLANA is a Token-2022 asset with both mint and freeze authorities successfully revoked, ensuring supply immutability and protection against account freezing. The token exhibits healthy liquidity levels and no adverse flags from third-party registries. Holder concentration data was unavailable, and metadata remains mutable, which should be monitored by potential users.

> **Final Recommendation:** Investors should verify the current metadata on-chain to ensure it matches expected branding, as the metadata remains mutable. Since holder concentration data is unavailable, users should monitor large wallet movements via block explorers to identify potential sell-side pressure.

Regularly check the mint address on-chain to confirm that authority flags remain revoked. No further technical action is required as the core security parameters are correctly configured.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program, providing advanced extension capabilities. 7.1 Architecture is standard for SPL tokens, with no active transfer hooks or default frozen states. 7.3 Access… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic stability is supported by $155,495 in liquidity and a healthy 0.63 volume/liquidity ratio. 7.5 Governance and 7.8 Operations are decentralized due to the revocation of administrative… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not applicable to SPL mints in the traditional sense. Metadata is currently mutable (7.3), allowing for potential updates to the token name or symbol. No other mutable extensions or… |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable, meaning it can be changed by the original deployer at any time.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $215K (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $215K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GF74fB...Nyk6`](https://solscan.io/account/GF74fBfcaeLjUiUwKpRiUbvMQtTvNyzMoo6KNyyqNyk6) |
| **Network** | Solana |
| **Price** | $0.0004841 |
| **24h Volume** | $81.8K |
| **Liquidity** | $153.7K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 8h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 911 buys / 867 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/citm89hmcbhg4smnxrtjzayb9xbnv94eekhaktempktm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stonklana-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
