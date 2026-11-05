---
token: 九运元亨币 
ticker: 九运元亨币 
network: bsc
risk_score: 21
status: low
date: 2026-11-05
---

# 九运元亨币  (九运元亨币 ) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-a0f433-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a standard ERC-20 token deployed as an EIP-1167 minimal clone. The contract ownership has been renounced, effectively locking the administrative functions and preventing any further changes to the migration state or tax parameters. The codebase follows standard OpenZeppelin patterns for token implementation. No vulnerabilities were identified in the provided logic.

> **Final Recommendation:** The contract is currently in a secure, immutable state. No further action is required for the security of the token logic. Users should continue to monitor the token's market activity and liquidity pool interactions, as these are independent of the token contract's internal security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes EIP-1167 minimal clones to minimize deployment costs while maintaining standard ERC-20 functionality. 7.1 Architecture is robust and immutable due to the clone pattern. 7.2… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic parameters are fixed as the migration functions are no longer callable. 7.5 Governance is non-existent due to the renounced ownership, ensuring no central party can manipulate token… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not applicable as this is an EIP-1167 minimal clone, which is inherently immutable. The implementation logic is fixed at the time of deployment. 7.8 Operations are stable, as the… |

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

The ten largest holders own 50.3% of supply. Of that, 33.9% burned — not holders that can sell, so excluded from the concentration score. What remains: 6.0% in wallets, 10.4% in other contracts. 1,545 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,545 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $40K (DexScreener, all pools). 24h trading volume $256K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 2.97% on sell. Market: $40K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd07c...7777`](https://bscscan.com/address/0xd07c109207534b0cd4dda92ba50c185545fb7777) |
| **Network** | BNB Chain |
| **Price** | $0.0001935 |
| **24h Volume** | $255.4K |
| **Liquidity** | $40.1K |
| **Volume / Liquidity** | 6.4× |
| **Token Age** | 14h |
| **Top-10 Holders** | 50.3% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 2765 buys / 2078 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xf191efb661fcbf1b4894028f7abd81bfbced023f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-a0f433-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
