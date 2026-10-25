---
token: Binance AI
ticker: BIBI
network: bsc
risk_score: 70
status: high
date: 2026-10-25
---

# Binance AI (BIBI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binance-ai-bsc-0a28)

---

## Audit Summary

The audited contract is a standard ERC-20 token implementation. It follows the OpenZeppelin-style pattern for token management and contains no privileged administrative functions, backdoors, or complex logic. The code is straightforward and adheres to established industry standards for fungible tokens.

> **Final Recommendation:** The contract is secure and follows standard implementation patterns. No further action is required for the current codebase.

Users should always verify the contract address on the block explorer before interacting with it to ensure they are engaging with the intended token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows a standard ERC-20 implementation (7.1 Architecture). Code security is high due to the use of well-vetted libraries (7.2 Code Security). There are no access control mechanisms… |
| **Governance / Economics** | 1/10 | High | There are no economic parameters or governance mechanisms defined in the contract (7.4 Economic, 7.5 Governance). The token operates as a simple store of value without external dependencies (7.6… |
| **Upgrades** | 6/10 | Medium | The contract is not upgradeable. It does not utilize proxy patterns or delegatecall mechanisms. Consequently, there is no risk associated with contract upgrades or logic changes. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xb962…182d) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 12.2% of supply. Of that, 2.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 10.2% in wallets, 0.0% in other contracts. 1,346 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,346 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $76K (DexScreener, all pools). 24h trading volume $2.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $76K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xde75...eb0d`](https://bscscan.com/address/0xde753c312d7a54a3c37a704a4b082d7d265beb0d) |
| **Network** | BNB Chain |
| **Price** | $0.001972 |
| **24h Volume** | $2.50M |
| **Liquidity** | $76.0K |
| **Volume / Liquidity** | 32.9× |
| **Token Age** | 6h |
| **Top-10 Holders** | 12.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4437 buys / 3378 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x2571362ae13c7698208cc10a8bfa5921cb1b033c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binance-ai-bsc-0a28)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
