---
token: 笑傲江湖
ticker: 笑傲江湖
network: bsc
risk_score: 15
status: low
date: 2026-10-21
---

# 笑傲江湖 (笑傲江湖) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-be65f3-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) of an ERC-20 token implementation. The contract ownership has been renounced, effectively disabling all privileged administrative functions. The architecture is immutable, and the token logic is standard, posing minimal risk to users.

> **Final Recommendation:** The contract is secure due to its immutable nature and renounced ownership. No further action is required for the current deployment.

Users should verify the contract address against official documentation to ensure they are interacting with the intended token instance, as the minimal clone pattern is widely used.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a standard EIP-1167 minimal clone pattern, ensuring consistent logic deployment. 7.1 Architecture and 7.2 Code Security are robust due to the use of well-audited OpenZeppelin… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance risks are mitigated by the renounced ownership, preventing any further changes to the tax or migration state. The token operates on a fixed logic path defined at the… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not possible for this contract as it is a minimal clone. The implementation is fixed at the bytecode level, providing high security against upgrade-related vulnerabilities. 7.8… |

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

The ten largest holders own 49.9% of supply. Of that, 30.7% locked, 12.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.2% in wallets, 3.7% in other contracts. 3,643 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,643 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $39K (DexScreener, all pools). 24h trading volume $182K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 4% on sell. Market: $39K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8ef7...7777`](https://bscscan.com/address/0x8ef757d44ed5f71e17ef8d8d52448b3dc8107777) |
| **Network** | BNB Chain |
| **Price** | $0.0001562 |
| **24h Volume** | $151.0K |
| **Liquidity** | $38.8K |
| **Volume / Liquidity** | 3.9× |
| **Token Age** | 18h |
| **Top-10 Holders** | 49.9% of supply |
| **Buy / Sell Tax** | 3.0% / 4.0% |
| **24h Transactions** | 4823 buys / 911 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xbe22d15779681f94095d610a49dc39a11a7e76dd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-be65f3-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
