---
token: bInference
ticker: BINF
network: bsc
risk_score: 12
status: low
date: 2026-10-06
---

# bInference (BINF) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binference-bsc)

---

## Audit Summary

This audit covers the FlapTaxTokenV3 contract, an ERC-20 token with additional tax and anti-farmer mechanisms. The contract is deployed as an EIP-1167 minimal clone, meaning its logic is immutable and cannot be upgraded. Ownership of the contract has been renounced, effectively disabling all owner-restricted functions, including those that modify the token's tax and anti-farmer states. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** Ensure all external integrations and user interfaces accurately reflect the current, immutable state of the FlapTaxTokenV3 contract, particularly regarding its fixed tax and anti-farmer mechanisms. Given that ownership has been renounced and the contract is not upgradeable, the token's behavior is permanently set. Users should be aware that no further administrative changes to the token's core logic or economic parameters are possible.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The FlapTaxTokenV3 contract implements the ERC-20 standard, including `transfer`, `transferFrom`, `approve`, and `balanceOf` functions, ensuring standard token functionality (7.2 Code Security). It… |
| **Governance / Economics** | 7/10 | Low | The economic model of FlapTaxTokenV3 includes configurable tax and anti-farmer mechanisms, controlled by the `poolState` variable. These mechanisms were intended to be managed via `startMigration()`… |
| **Upgrades** | 9/10 | Low | The FlapTaxTokenV3 contract is deployed as an EIP-1167 minimal clone, which means its bytecode points to a fixed implementation address (7.1 Architecture). This design choice makes the contract… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xddac…308c — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 31.7% of supply. Of that, 6.0% burned — not holders that can sell, so excluded from the concentration score. What remains: 7.4% in wallets, 18.3% in other contracts. 1,493 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,493 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $130K (DexScreener, all pools). 24h trading volume $628K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 2.97% on sell. Market: $130K of DEX liquidity across 2 pools. Launch: 5 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9862...7777`](https://bscscan.com/address/0x9862d6478cb8098645815ff27f91efbc659f7777) |
| **Network** | BNB Chain |
| **Price** | $0.001535 |
| **24h Volume** | $628.3K |
| **Liquidity** | $130.0K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 5d |
| **Top-10 Holders** | 31.7% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 1447 buys / 1223 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x25ee4fa4bff5363d47496e68377b1241e8e21a47)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binference-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
