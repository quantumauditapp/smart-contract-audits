---
token: 亮剑人生
ticker: 亮剑人生
network: bsc
risk_score: 10
status: low
date: 2026-10-29
---

# 亮剑人生 (亮剑人生) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-52e57e-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a standard ERC-20 token deployed as an EIP-1167 minimal clone. The contract ownership has been renounced on-chain, effectively disabling all privileged administrative functions. The token logic is immutable and cannot be upgraded or altered by any party. No vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The protocol is currently in a secure, immutable state due to the renouncement of ownership. No further action is required for the smart contract logic as it is locked and cannot be modified.

Users should remain aware that while the contract logic is immutable, the token's economic utility depends on the initial configuration set during deployment. Ensure that the token's behavior aligns with expectations before interacting with the liquidity pools.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes a robust EIP-1167 minimal clone pattern, ensuring consistent logic across deployments. Code security is maintained through the use of standard OpenZeppelin libraries for… |
| **Governance / Economics** | 7/10 | Low | Economic parameters are fixed due to the renouncement of ownership. 7.4 Economic and 7.5 Governance risks are mitigated as no entity can modify the pool state or tax parameters. The token functions… |
| **Upgrades** | 9/10 | Low | The contract is deployed as an immutable minimal clone, meaning 7.7 Upgrades are not applicable. The implementation logic is fixed at the time of deployment and cannot be redirected. This provides… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x14e5…be4a — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 87% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 87.9% of supply. Of that, 76.5% burned — not holders that can sell, so excluded from the concentration score. What remains: 2.2% in wallets, 9.2% in other contracts. 1,841 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,841 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $78K (DexScreener, all pools). 24h trading volume $528K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 0.99% on sell. Market: $78K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x01a8...7777`](https://bscscan.com/address/0x01a851f368d2df6ec89110ff20a2ac7bd2787777) |
| **Network** | BNB Chain |
| **Price** | $0.0006256 |
| **24h Volume** | $527.5K |
| **Liquidity** | $67.6K |
| **Volume / Liquidity** | 7.8× |
| **Token Age** | 11h |
| **Top-10 Holders** | 87.9% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 7223 buys / 2007 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xfda1adf76021aa1b88b110d43d98de9576d90bce)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-52e57e-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
