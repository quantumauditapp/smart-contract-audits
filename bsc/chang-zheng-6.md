---
token: Chang Zheng 6
ticker: 长征六号
network: bsc
risk_score: 20
status: low
date: 2026-10-24
---

# Chang Zheng 6 (长征六号) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chang-zheng-6-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone token contract. Ownership has been renounced on-chain, effectively locking the administrative functions. The contract implements standard ERC-20 functionality with additional migration-based state transitions. No vulnerabilities were identified in the current implementation.

> **Final Recommendation:** The protocol is in a secure, immutable state due to the renunciation of ownership. No further action is required for the current deployment. Users should note that the contract logic is fixed and cannot be adjusted to address future market conditions or bugs.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes a gas-efficient EIP-1167 minimal clone pattern. Code security is robust, adhering to standard OpenZeppelin patterns for ERC-20 and access control. 7.1 Architecture and 7.2… |
| **Governance / Economics** | 7/10 | Low | Governance is effectively nullified due to the renounced ownership status. 7.3 Access Control and 7.5 Governance are secure as no entity can modify the poolState or tax parameters. 7.4 Economic… |
| **Upgrades** | 10/10 | Low | The contract is deployed as an EIP-1167 minimal clone, which is inherently immutable. 7.7 Upgrades are not applicable as the logic cannot be changed or redirected. This eliminates risks associated… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 56.6% of supply. Of that, 43.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 12.8% in wallets, 0.0% in other contracts. 11,906 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

11,906 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $212K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $11K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2911...7777`](https://bscscan.com/address/0x2911de6cdff51f41ed7b33ee999249b3fac47777) |
| **Network** | BNB Chain |
| **Price** | $0.00001269 |
| **24h Volume** | $177.2K |
| **Liquidity** | $11.2K |
| **Volume / Liquidity** | 15.9× |
| **Token Age** | 11h |
| **Top-10 Holders** | 56.6% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 4341 buys / 1778 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x53a1e57d0272084b67444f67b159a619b8e5b01c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chang-zheng-6-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
