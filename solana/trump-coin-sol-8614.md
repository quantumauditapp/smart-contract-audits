---
token: Trump coin
ticker: TRUMPCOIN
network: solana
risk_score: 21
status: low
date: 2026-11-07
---

# Trump coin (TRUMPCOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trump-coin-sol-8614)

---

## Audit Summary

The Trump coin (TRUMPCOIN) mint has successfully revoked both mint and freeze authorities, ensuring supply immutability and preventing account freezing. Liquidity is highly secure with 99.7% burned or locked. Holder concentration data was unavailable, and metadata remains mutable, which is the primary security concern.

> **Final Recommendation:** Investors should monitor the token metadata for unexpected changes given its mutability. Due to the high volume/liquidity ratio, exercise caution regarding potential artificial trading volume when assessing market depth.

Verify the current metadata state via a block explorer to ensure it aligns with expected branding. No further on-chain action is required regarding authorities as they are already revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL-Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic stability is supported by 99.7% of liquidity being locked. 7.5 Governance is decentralized due to authority revocation. However, 7.6 External signals indicate a high volume/liquidity… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint. Metadata is mutable, allowing for potential branding changes. No other upgradeable extensions are active. |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 37.68, which exceeds the 20x threshold, indicating a pattern associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting trading volume as a signal of genuine market interest.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed by the owner at any time.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

99.6% of the pool's LP is burned or time-locked. 99.6% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 0.4% is held, unlocked, by 2 address(es) other than the pool's creator.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $14K (DexScreener, all pools). 24h trading volume $568K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $14K of DEX liquidity across 5 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EZr3za...BAGS`](https://solscan.io/account/EZr3zaL9oojKAtpNUYEihk4zWoZxbcKrNUM6SjEeBAGS) |
| **Network** | Solana |
| **Price** | $0.00003134 |
| **24h Volume** | $455.1K |
| **Liquidity** | $13.9K |
| **Volume / Liquidity** | 32.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8048 buys / 5004 sells |

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

## Sources

- [View on DexScreener](https://dexscreener.com/solana/abmu8jpd7row945h27xzznrhsoaqem7cipn1vfpmfdzh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trump-coin-sol-8614)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
